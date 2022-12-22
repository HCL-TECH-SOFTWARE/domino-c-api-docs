




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




**Initial Release 5.0.2**



**Function : Address Book; Domino
Directory**



**NAMELocateNextMatch2** **- Locate
the next match in a record in a look up buffer**


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**



void
far \* LNPUBLIC **NAMELocateNextMatch2(**  

      void far \*pLookup,  

      void far \*pName,  

      void far \*pMatch**);**



**Description :**



This function
is an enhanced 32-bit version of NAMELocateNextMatch. 


 


**Note:** Address
books refer to both Notes Client Address books, and Domino Server Address books
know as Domino Directories.


 


       This
routine finds the next match in a record in a look up buffer. One record in a
look up buffer contains all the matches in one view for a specified name. Use
this function to iterate over multiple matches when a call to NAMELookup2
yields more than one match for a given name.   

  

NAMELookup2 creates and initializes a look up buffer containing information
from the Address book(s). The look up buffer consists of a header (type
LOOKUP\_HEADER) followed by a series of records. The number of records is equal
to the number of views searched times the number of names looked up. A record
will contain multiple matches to a given name if the name matches more than one
document in a single view. First use NAMELocateNextName2 to locate the next
record in the buffer. Then use NAMELocateNextMatch2 to iterate over the matches
within one record.  

  

Call NAMELocateNextMatch2 in a loop to locate all the matches in a record.
Specify pMatch = NULL on the first iteration to locate the first match. Specify
pMatch = the location of the last match on subsequent iterations. Locate
individual items within a match by passing the location of the match as input
to NAMELocateItem2.  

  

Note: this routine depends on the caller knowing when to terminate the loop.
Use NumMatches as returned by NAMELocateNextName2 to control looping. The value
returned by this funciton is undefined if pMatch, on input, specifies the last
match in the record.


 


**Parameters :**



Input :  

pLookup  -   Address of a look up buffer containing information returned from
NAMELookup2. NAMELookup2 returns a handle. Call OSLockObject on the handle to
obtain this address.  

  

pName  -  Location of a record corresponding to one name in the look up buffer.
Use NAMELocateNextName2 to obtain this location.  

  

pMatch  -  Location of previous match in the record. Specify NULL to locate the
first match in the record. NAMELocateNextMatch returns a pointer to the next
record in the buffer that matches the specified name. NULL is NOT returned to
indicate termination.  

  




Output :  

(routine)  -  Address of the next match in the record in a look up buffer.   

  

  




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

    error = NAMELookup2(pMailServerName,         /\* Ptr to mail server name \*/  

                          0,                                    /\* Flags -
DWORD \*/  

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

  

           pName = NAMELocateNextName2(pLookup, pName, &NumMatches);  

  

           /\*      Traverse all matches for this name \*/  

  

           for (pMatch = NULL, j = 0; j < NumMatches; j++)  

                   {  

                   pMatch = NAMELocateNextMatch2(pLookup, pName, pMatch);  

  

                   /\*      Here, handle a simple (non-list) item for this match
\*/  

  

                   pDomain = NAMELocateItem2(pMatch, ITEM\_DOMAIN,
&DataType, &Size);  

                   if (pDomain == NULL)          /\* if item not present in this
match \*/  

                          continue;                             /\* go on to next
match \*/  

  

                   /\*      Here, handle a text list or text item (this handles  

                          both kinds) and traverse all members \*/  

  

                   for (k = 0; ; k++)  

                          {  

                          if (NAMEGetTextItem2(pMatch, ITEM\_MEMBERS, k,   

                                                        Buffer, sizeof(Buffer))
!= NOERROR)  

                                  break;  

                          }  

                   }  

           }  

    OSUnlockObject(hLookup);  

OSMemFree(hLookup);


 **See Also :**


**[NAMEGetTextItem2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A037D015E98CD0DA8525680F005C8B14)**


**[NAMELocateItem2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C3B8D7B0F1E9A1B88525680F005C5DFA)**


**[NAMELocateNextMatch](NAMELocateNextMatch.md)**


**[NAMELocateNextName2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E97CC057B405B358525680F005C021E)**


**[NAMELookup2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7B7DBB5F82E0197E482573FB00323579)**


**[OSLockObject](OSLockObject.md)**



----------------------------------------------------------------------------------------------------------


 





