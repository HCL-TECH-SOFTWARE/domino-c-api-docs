




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




 


**Data Type : Composite Data; Rich
Text**



**CDOLEEND** **-** Specifies
the end of an OLE Object.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header; /\* Signature and length of this record \*/         

   DWORD Flags; /\* Currently unused, but reserve some flags \*/  

}CDOLEEND;


 


**Description :**



This
structure specifies the end of an OLE Object in a rich text field.  

  

Note that rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.


 **See Also :**


**[CDOLEBEGIN](CDOLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





