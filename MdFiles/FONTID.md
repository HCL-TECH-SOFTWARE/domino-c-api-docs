




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




 


**Data Type : Rich Text**



**FONTID** **-** Controls how
text is displayed in Rich Text.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



typedef DWORD FONTID;


 


**Description :**



Identifier
used to select a particular font to be used when displaying a portion of a Rich
Text item.  Each portion or 'text run' you construct may reference any one of
the commonly available typefaces used by the Notes workstation application.  If
you are dealing with existing Rich Text, then the typeface was probably established
by the form designer, another API application, or the latest document author.    

  

The particular font value is contained in one byte of the FONTID portion of the
header of each CDTEXT record.  Other bytes in the FONTID control the point
size, display attributes, and color to be used.  For a description of these
fields, see the entry FONTIDFIELDS.  The Notes workstation application uses
this information to present each text run in each Rich Text field of a
document.  There are several convenient macros in FONTID.H that allow you to
modify the individual bits of a FONTID, thereby controlling how text will be
displayed.


 **See Also :**


**[CDTEXT](CDTEXT.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[xxx\_FONT\_ID](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5026A4E5153414BF85256258005EA4EA)**



----------------------------------------------------------------------------------------------------------


 





