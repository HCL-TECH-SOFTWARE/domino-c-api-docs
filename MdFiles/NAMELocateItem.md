




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



**NAMELocateItem** **- Locate an
item value in a record in a look up buffer**


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**



void
far \* LNPUBLIC **NAMELocateItem(**  

      void far \*pMatch,  

      WORD  Item,  

      WORD far \*retDataType,  

      WORD far \*retSize**);**



**Description :**



This routine
gets information about an item in a look up buffer. It gets the location of the
item value, the data type word, and value length. Use this function to get
information about an item in a look up buffer returned from NAMELookup.   

  

If the item is of TYPE\_TEXT or TYPE\_TEXT\_LIST, use NAMEGetTextItem rather than
this routine to retrieve text from the buffer.  

  

NAMELookup creates and initializes a look up buffer containing information
about a series of names. The buffer consists of a series of records, one record
per name. A record may contain multiple matches to a given name. A match may
contain multiple item values if multiple items were requested in the NAMELookup
call. See NAMELookup arguments "Items" and "NumItems".  

  

After NAMELookup returns the buffer, use NAMELocateNextName to locate the next
record in the buffer. Use NAMELocateNextMatch to locate one match in the
record. Then use NAMELocateItem to get information about a specific item in the
match.   

  

Use the zero-based item number to specify one item in the match. The item
number is the index of the item in the series of items specified in the
"Items" argument to NAMELookup. 


 


**Parameters :**



Input :  

pMatch  -  address of a match in a look up buffer. Get this address by calling
NameLocateNextMatch.  

  

Item  -  Item number = index of the item name in the set specified by the
"Items" argument to NAMELookup. Zero specifies the first item. Note:
this item number must not be greater than the number of items specified by the
"NumItems" argument to NAMELookup.  

  




Output :  

(routine)  -  pointer to an item value in a look up buffer. NULL indicates the
item is not present in the match. Item value begins with the data type word.
However, caller can not directly de-reference this pointer to retrieve the data
type word as it may be odd aligned. The data type word is returned separately.  

  

  

retDataType  -  receives the data type word of the requested item (e.g.
TYPE\_TEXT).  

  

retSize  -  receives the data length, in bytes, of the requested item value,
including the data type word.  

  




 **Sample Usage :**


#define USERNAMESSPACE
"$Users"  

#define Names                     "Bill Smith\0Ted Jones\0Marketing"  

#define MAIL\_LOOKUPITEMS
"Domain\0Server\0PublicKey\0Members\0Certificate"  

#define ITEM\_DOMAIN               0  

#define ITEM\_SERVER               1  

#define ITEM\_PUBLICKEY    2  

#define ITEM\_MEMBERS      3  

#define    ITEM\_CERTIFICATE 4  

      

    NumNames = 3;                                               /\* 3 names to
look up \*/  

    NumItems = 5;  

    error = NAMELookup(pMailServerName,          /\* Ptr to mail server name \*/  

                                  0,                                    /\*
Flags \*/  

                                  1,                                    /\*
Number of name spaces \*/  

                                  USERNAMESSPACE,               /\* Name of name
space (view name) \*/  

                                  NumNames,                    /\* # of names
\*/  

                                  Names,                        /\* Ptr to the
names themselves \*/  

                                  NumItems,                     /\* # of items
desired \*/  

                                  MAIL\_LOOKUPITEMS,      /\* Ptr to the item
names \*/  

                                  &hLookup);                    /\*  Handle
of returned buffer \*/  

    if (error)  

           goto Abort;  

  

    pLookup = OSLockObject(hLookup);  

  

    /\*      For each name requested, traverse the results for each name \*/  

  

    for (pName = NULL, i = 0; i < NumNames; i++)  

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

OSMemFree (hLookup);


 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[NAMELocateNextName](NAMELocateNextName.md)**


**[NAMELocateNextMatch](NAMELocateNextMatch.md)**


**[NAMEGetTextItem](NAMEGetTextItem.md)**


**[OSLockObject](OSLockObject.md)**



----------------------------------------------------------------------------------------------------------


 





