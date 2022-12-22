




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




**Initial Release 4.6**



**Data Type : Rich Text; Composite
Data**



**CDHRULE** **-** Horizontal
line.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header; /\* Signature and length of this record. \*/  

   DWORD Flags;      

   WORD  Width;  

   WORD  Height;  

   WORD  Color;  

   WORD  GradientColor;  

} CDHRULE;


 


**Description :**



Specifies a
horizontal line.  The fields in this structure are:


 


Header             Defines
this composite data item as a CDHRULE item.  

Flags                Optional flags;  see HRULE\_FLAG\_xxx for flag values.  

Width               Specifies the horizontal length of the line in TWIPS (see
the symbolic definition for ONEINCH for more information).  Use DEFAULTHRULEWIDTH
for the default.  

Height              Specifies the height of the line (or thickness) in TWIPS. 
Use DEFAULTHRULEHEIGHT for the default.


Color                Specifies
the color used to draw the line (see the symbolic values for NOTES\_COLOR\_xxx
for more information).  

GradientColor   Specifies the gradient color used to draw the line (see the
symbolic values for NOTES\_COLOR\_xxx for more information).


 


 **See Also :**


**[CDHORIZONTALRULE\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/510A4C5E81862CF385256678004A6B7A)**


**[DEFAULTHRULExxx](DEFAULTHRULExxx.md)**


**[HRULE\_FLAG\_xxx](HRULE_FLAG_xxx.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**


**[ONEINCH](ONEINCH.md)**



----------------------------------------------------------------------------------------------------------


 





