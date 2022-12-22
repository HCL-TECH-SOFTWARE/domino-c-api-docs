




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



**Data Type : Composite Data; Rich
Text**



**CDDATAFLAGS** **-** Collapsible
section, button type, style sheet or field limit information for Notes/Domino
6.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    BSIG    Header;  

    WORD    nFlags;        /\* number of flags \*/  

    WORD    elemType;              /\* element these flags are for,
CD\_xxx\_ELEMENT \*/  

    DWORD   dwReserved;            /\* future \*/  

    /\* DWORDS of flags follow... \*/  

} CDDATAFLAGS;


 


 


**Description :**



Contains
collapsible section, button type, style sheet or field limit information for
Notes/Domino 6. A CD record (CDBAR, CDBUTTON, CDBORDERINFO, CDFIELDHINT, etc.)
may be followed by a CDDATAFLAGS structure. 


  

The fields in this structure are:  

  




Header - Defines
this composite data item as a CDDATAFLAGS item.


 


nFlags -
Number of flags.  


 


elemType -
CD\_SECTION\_ELEMENT, CD\_BUTTONEX\_ELEMENT or CD\_FIELDLIMIT\_ELEMENT


 


dwReserved -
Future use.


 


If the value
of the nFlags member is greater than zero, then immediately following this
structure there will be n DWORD Flags that identify the value of the Flags data
border, button type, style sheet or field limit.  You can use the macros
GETDATABORDERTYPE and SETDATABORDERTYPE to get and set each of the Flags.


 


  
If elemType is CD\_FIELDLIMIT\_ELEMENT, you can use Flag &
FIELD\_LIMIT\_TYPE\_XXX is not zero to get the limit type.  See
FIELD\_LIMIT\_TYPE\_XXX.


 


Note that
CDDATAFLAGS records reside in items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these
records in an item in a note.


 **See Also :**


**[BARREC\_DATA\_BORDER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/90ADB3E4E2033454852569D700621122)**


**[BUTTON\_TYPE\_xxx](BUTTON_TYPE_xxx.md)**


**[CDBAR](CDBAR.md)**


**[CDBUTTON](CDBUTTON.md)**


**[CDFIELDHINT](CDFIELDHINT.md)**


**[CD\_xxx\_ELEMENT](CD_xxx_ELEMENT.md)**


**[GETDATABORDERTYPE](GETDATABORDERTYPE.md)**


**[SETDATABORDERTYPE](SETDATABORDERTYPE.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





