




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




 


**Symbolic Value : Item (Field)
Information**



**ITEM\_xxx [READWRITERS]** **-** Item Data
Type - Author Names


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



**Description :**



Author Names
fields have external (field definition) data type "Author Names". 
Domino grants author access to any entity named in an Author Names field.  

  

At the API level, an Author Names field is an item of TYPE\_TEXT or
TYPE\_TEXT\_LIST with both the NAMES flag set and the READ/WRITE-ACCESS flag
set.  The NAMES flag corresponds to the ITEM\_NAMES bit in the item flags.  The
READ/WRITE-ACCESS flag corresponds to the ITEM\_READWRITERS bit in the item
flags.  

  

Since the API function NSFItemSetText does not set the ITEM\_READWRITERS flag,
use NSFItemAppend to append Author Names fields to documents.


 **Sample Usage :**


STATUS  LNPUBLIC 
AppendEditorsItem (NOTEHANDLE  hNote)  

{  

    STATUS      error = NOERROR;  

    DWORD       dwValueLen;  

    void far   \*pvoidItemValue;  

    LIST       \*pList;  

    USHORT     \*pusLength;  

    USHORT      usLen1, usLen2;  

    char       \*pchStr;  

  

#define EDITORS1        "NADC Executives"  

#define EDITORS2        "NADC Marketing"  

#define EDITORS\_COUNT   2  

  

    usLen1 = strlen(EDITORS1);  

    usLen2 = strlen(EDITORS2);  

  

    dwValueLen = sizeof(LIST) + (EDITORS\_COUNT \* sizeof(USHORT)) +  

                 usLen1 + usLen2 ;  

  

    pvoidItemValue = (void far \*) malloc ((size\_t)dwValueLen);  

  

    pList = (LIST\*)pvoidItemValue;  

    pList->ListEntries = EDITORS\_COUNT;  

    pList++;  

    pusLength = (USHORT\*)pList;  

    \*pusLength = usLen1;  

    pusLength++;  

    \*pusLength = usLen2;  

    pusLength++;  

    pchStr = (char\*)pusLength;  

    memcpy (pchStr, EDITORS1, usLen1);  

    pchStr += usLen1;  

    memcpy (pchStr, EDITORS2, usLen2);  

  

    if (error = NSFItemAppend ( hNote,   

                                ITEM\_SUMMARY | ITEM\_READWRITERS | ITEM\_NAMES,  

                                DISCUSS\_ITEM\_EDITORS,  /\* "Editors"
\*/  

                                strlen(DISCUSS\_ITEM\_EDITORS),  

                                TYPE\_TEXT\_LIST,  

                                pvoidItemValue,  

                                dwValueLen))  

    {  

        printf ("Error: unable to append Editors field.\n");  

    }  

    free (pvoidItemValue);  

    return (error);  

}


 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[ITEM\_xxx [NAMES]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/557B87BE33862F688525623800493995)**


**[ITEM\_xxx [READERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0134426255B7EE1885256238004A727D)**



----------------------------------------------------------------------------------------------------------


 





