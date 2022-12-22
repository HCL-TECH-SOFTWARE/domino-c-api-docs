




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



**ITEM\_xxx [READERS]** **-** Item Data
Type - Reader Names


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



**Description :**



Reader Names
fields have external data type "Reader Names".  Domino grants reader
access to any entity named in a Reader Names field.  

  

At the API level, a Reader Names field is an item of TYPE\_TEXT or
TYPE\_TEXT\_LIST with both the NAMES flag set and the READ-ACCESS flag set.  The
NAMES flag corresponds to the ITEM\_NAMES bit in the item flags.  The
READ-ACCESS flag corresponds to the ITEM\_READERS bit in the item flags.  

  

Since the API function NSFItemSetText does not set the ITEM\_READERS flag, use
NSFItemAppend to append Reader Names fields to documents.


 **Sample Usage :**


STATUS  LNPUBLIC 
AppendReadersItem (NOTEHANDLE  hNote)  

{  

    STATUS      error = NOERROR;  

    DWORD       dwValueLen;  

    void far   \*pvoidItemValue;  

    LIST       \*pList;  

    USHORT     \*pusLength;  

    USHORT      usLen1, usLen2;  

    char       \*pchStr;  

  

    usLen1 = strlen(READERS1);  

    usLen2 = strlen(READERS2);  

  

    dwValueLen = sizeof(LIST) + (READERS\_COUNT \* sizeof(USHORT)) +  

                 usLen1 + usLen2 ;  

  

    pvoidItemValue = (void far \*) malloc ((size\_t)dwValueLen);  

    if (pvoidItemValue == NULL)  

    {  

        printf ("Error: unable to allocate %lu bytes memory.\n",
dwValueLen);  

        return(ERR\_V3AUTHOR\_MALLOC);  

    }  

  

    pList = (LIST\*)pvoidItemValue;  

    pList->ListEntries = READERS\_COUNT;  

    pList++;  

    pusLength = (USHORT\*)pList;  

    \*pusLength = usLen1;  

    pusLength++;  

    \*pusLength = usLen2;  

    pusLength++;  

    pchStr = (char\*)pusLength;  

    memcpy (pchStr, READERS1, usLen1);  

    pchStr += usLen1;  

    memcpy (pchStr, READERS2, usLen2);  

  

    if (error = NSFItemAppend ( hNote,   

                                ITEM\_SUMMARY | ITEM\_READERS | ITEM\_NAMES,  

                                DISCUSS\_ITEM\_READERS,  /\* "Readers"
\*/  

                                strlen(DISCUSS\_ITEM\_READERS),  

                                TYPE\_TEXT\_LIST,  

                                pvoidItemValue,  

                                dwValueLen))  

    {  

        printf ("Error: unable to append Readers field.\n");  

    }  

    free (pvoidItemValue);  

    return (error);  

}


 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[ITEM\_xxx [NAMES]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/557B87BE33862F688525623800493995)**


**[ITEM\_xxx [READWRITERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2175B1F1F4585C4852562380049DF01)**



----------------------------------------------------------------------------------------------------------


 





