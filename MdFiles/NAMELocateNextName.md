




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Address Book; Domino
Directory**



**NAMELocateNextName** **- Locate
the next record in a look up buffer**


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**



void
far \* LNPUBLIC **NAMELocateNextName(**  

      void far \*pLookup,  

      void far \*pName,  

      WORD far \*retNumMatches**);**



**Description :**



This routine
finds the next record in a look up buffer. A look up buffer is created by a
call to NAMELookup. A look up buffer contains a series of records. Each record
contains information about one name from one view in an Address book or Domino
Directory (Server's Address book).  

  

The number of records in a look up buffer is equal to the number of views
searched times the number of names looked up. Each record may contain multiple
matches for the given name if multiple documents in the view match the name.
NAMELocateNextName finds the next record (or the first record) in the buffer
and returns the name itself and the number of matches in the record.  

  

Use this function to find the next record in a buffer created by NAMELookup,
and to determine how many matches NAMELookup found for that name in that view.  

  

Call NAMELocateNextName in a loop to process each record in the buffer created
by NAMELookup. Specifying pName = NULL on the first iteration to get the record
for the first match. and the value returned from NAMELocateNextName on each
subsequent iteration. Execute the loop for each record in the buffer.


 


**Parameters :**



Input :  

pLookup  -  Address of a look up buffer containing information returned from
NAMELookup. NAMELookup returns a handle. Call OSLockObject on the handle to
obtain this address.  

  

pName  -  Previous record in the buffer. Specify NULL to locate the first
record in the buffer.  

  




Output :  

(routine)  -  The next record in the look up buffer. If pName is NULL on input,
then this returns the first record in the buffer. If pName specifies the last
record in the buffer, then this returns NULL.  

  

  

retNumMatches  -  Receives the number of matches in the next record. If
NAMELookup finds more than one match for a given name in a given view, then the
record corresponding to that name in that view contains more than one match.  

  




 **Sample Usage :**


#define USERNAMESSPACE
"$Users"  

#define NUM\_NAME\_SPACES 1  

#define Names             "Bill Smith\0Ted Jones\0Marketing"  

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

                                                        Buffer, sizeof(Buffer))
!= NOERROR)  

                                  break;  

                          }  

                   }  

           }  

    OSUnlockObject(hLookup);  

OSMemFree(hLookup);


 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[NAMELocateNextMatch](NAMELocateNextMatch.md)**


**[NAMELocateItem](NAMELocateItem.md)**


**[NAMEGetTextItem](NAMEGetTextItem.md)**


**[OSLockObject](OSLockObject.md)**



----------------------------------------------------------------------------------------------------------


 





