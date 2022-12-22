




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 6**



**Function : ASP**



**VDirContextInit** **- Scope
lookups in $Users by organization name (ASP enabled configurations only).**


**----------------------------------------------------------------------------------------------------------**



**#include <vdirctx.h>**



STATUS
LNPUBLIC **VDirContextInit(**  

      const char \*OrgName**);**



**Description :**



In a ASP
configuration, names in the $Users view are composed by combining the
organization name with the user or group name.  Therefore, lookups of names in
the $Users view requires both the organization name as well as the user or
group name.  To pass the organization name to the NAMELookup function, you must
use VDirContextInit to initialize a thread-static string with the organization
name.  Within the current thread, all future calls to NAMELookup will be scoped
by the organization name until VDirContextDestroy is called. 
VDirContextDestroy will release the thread-static memory.  You may call
VDirContextInit more than once to change the organization name, without calling
VDirContextDestroy between VDirContextInit calls.  If you do not call
VDirContextInit before looking up a name in $Users, the lookup will be scoped
by the server's organization name.  This call should be used in ASP
configurations only.


 


**Parameters :**



Input :  

OrgName  -  Organization name used to scope NAMELookups in $Users view.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully initialized the organization name  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **Sample Usage :**


#define USERNAMESSPACE
"$Users"  

#define NUM\_NAME\_SPACES 1  

#define Names             "Bill Smith\0Ted Jones\0Marketing"


    #define OrgName    "Org1"  

#define NUM\_NAMES  3  

#define MAIL\_LOOKUPITEMS
"Domain\0Server\0PublicKey\0Members\0Certificate"  

#define NUM\_LOOKUPITEMS 5  

#define ITEM\_DOMAIN               0  

#define ITEM\_SERVER               1  

#define ITEM\_PUBLICKEY    2  

#define ITEM\_MEMBERS      3  

#define    ITEM\_CERTIFICATE 4  

      

NumViews = NUM\_NAME\_SPACES;  

    NumNames = NUM\_NAMES;                                               /\* 3
names to look up \*/  

    NumItems = NUM\_LOOKUPITEMS;


        error =
VDirContextInit(OrgName);            /\* Setup the organization name before
calling NAMELookup \*/


        if (error)


               goto
Abort;


  

    error = NAMELookup(pMailServerName,          /\* Ptr to mail server name \*/  

                          0,                                    /\* Flags \*/  

                          1,                                    /\* Number of
name spaces \*/  

                          USERNAMESSPACE,               /\* Name of name space
(view name) \*/  

                          NumNames,                    /\* # of names \*/  

                          Names,                        /\* Ptr to the names
themselves \*/  

                          NumItems,                     /\* # of items desired
\*/  

                          MAIL\_LOOKUPITEMS,      /\* Ptr to the item names \*/  

                          &hLookup);                    /\*  Handle of
returned buffer \*/  

    if (error)  

           goto Abort;  

  

    pLookup = OSLockObject(hLookup);  

  

    /\*      For each name requested, traverse the results for each name \*/  

  

    for (pName = NULL, i = 0; i < (NumViews\*NumNames); i++)  

           {  

           /\*      Locate the set of matches for the next name searched for \*/  

  

           pName = NAMELocateNextName(pLookup, pName, &NumMatches);  

  

           /\*      Traverse all matches for this name \*/  

  

           for (pMatch = NULL, j = 0; j < NumMatches; j++)  

                   {  

                   pMatch = NAMELocateNextMatch(pLookup, pName, pMatch);  

  

                   /\*      Here, handle a simple (non-list) item for this match
\*/  

  

                   pDomain = NAMELocateItem(pMatch, ITEM\_DOMAIN, &DataType,
&Size);  

                   if (pDomain == NULL)          /\* if item not present in this
match \*/  

                          continue;                             /\* go on to
next match \*/  

  

                   /\*      Here, handle a text list or text item (this handles  

                          both kinds) and traverse all members \*/  

  

                   for (k = 0; ; k++)  

                          {  

                          if (NAMEGetTextItem(pMatch, ITEM\_MEMBERS, k,   

                                                         Buffer,
sizeof(Buffer)) != NOERROR)  

                                  break;  

                          }  

                   }  

           }  

    OSUnlockObject(hLookup);  

OSMemFree(hLookup);


    VDirContextDestroy();             /\*
Free the thread-static memory \*/


 **See Also :**


**[VDirContextDestroy](VDirContextDestroy.md)**



----------------------------------------------------------------------------------------------------------


 





