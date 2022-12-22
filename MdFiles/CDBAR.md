




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




**Initial Release 4.1**



**Data Type : Composite Data; Hotspot;
Rich Text**



**CDBAR** **-** Defines the
appearance of a collapsible section in a rich text field.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG    Header;  

   DWORD   Flags;  

   FONTID  FontID;  

/\* Caption and name follow \*/  

} CDBAR;


 


**Description :**



This
structure defines the appearance of the bar used with collapsible sections.


 


      Header:                  Defines
this composite data item as a CDBAR item.


      Flags:                     This
can be set to any of the values that begin with BARREC\_


      FontID:                   Specifies
the font, size, and color of the bar title. See FONTIDFIELDS for the definition
of FontID.


 


      If the
BARREC\_HAS\_COLOR bit is set in the Flags field then immediately following this
structure there will be a WORD that identifies the value of the color. This
color value comes from the defines in the file COLORID.H that begin with
NOTES\_COLOR\_xxx. If the BARREC\_ISFORMULA bit is set in the Flags field then the
next thing will be a formula, otherwise it will be the text of the title.


 


      For
collapsible sections indicated by a tab or a tab with a diagonal border, the
CDBAR record (with its Flags member set to BARREC\_BORDER\_OTHER) is followed by
a CDDATAFLAGS structure with its variable Flags data border set to
BARREC\_DATA\_BORDER\_TAB (for tab) or BARREC\_DATA\_BORDER\_DIAG (for diagonal). 


 


      Note
that CDBAR records reside in items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform host/canonical
conversion on structures of this type when accessing these records in an item
in a note.


 **See Also :**


**[BARREC\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2097E4EFE15F1641852563B50057C8AD)**


**[BAR\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/072A1D7A312DB99685256678004A471F)**


**[CDDATAFLAGS](CDDATAFLAGS.md)**


**[GETBORDERTYPE](GETBORDERTYPE.md)**


**[SETBORDERTYPE](SETBORDERTYPE.md)**



----------------------------------------------------------------------------------------------------------


 





