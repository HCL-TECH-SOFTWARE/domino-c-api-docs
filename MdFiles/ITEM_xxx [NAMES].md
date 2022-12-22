




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



**ITEM\_xxx [NAMES]** **-** Item Data
Type - Names


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



**Description :**



Use Names
fields to store distinguished (hierarchical) names.  Domino application
developers specify data type Names in the field definition of fields that will
store one or several distinguished names. The Names data type causes the Notes
workstation to display the fields in abbreviated format.  

  

Internally (at the API level) Names fields are stored as items of TYPE\_TEXT or
TYPE\_TEXT\_LIST marked with the distinguished names flag, ITEM\_NAMES.   

  

Since the API function NSFItemSetText does not set the ITEM\_NAMES flag, use
NSFItemAppend to append Names fields to documents.


 **Sample Usage :**


STATUS LNPUBLIC
AppendUpdatedByItem (NOTEHANDLE hNote, char \* szAuthor)  

{  

    STATUS  error;  

  

    if (error = NSFItemAppend ( hNote,   

                                ITEM\_SUMMARY | ITEM\_NAMES,  

                                DISCUSS\_ITEM\_$UPDATEDBY,  /\*
"$UpdatedBy" \*/  

                                strlen(DISCUSS\_ITEM\_$UPDATEDBY),  

                                TYPE\_TEXT,  

                                szAuthor,  

                                strlen(szAuthor)))  

    {  

        printf ("Error: unable to append $UpdatedBy field.\n");  

    }  

    return (error);  

}


 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[ITEM\_xxx [READERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0134426255B7EE1885256238004A727D)**


**[ITEM\_xxx [READWRITERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2175B1F1F4585C4852562380049DF01)**



----------------------------------------------------------------------------------------------------------


 





