




<!--
 /\* Font Definitions \*/
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




 


**Function : Canonical Format
Conversion**



**odsmacro** **- Define
ODS conversion symbol.**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



void **odsmacro(**  

      (any data type)  name,  

      int  num,  

      int  size**);**



**Description :**



This macro
is used to define conversion codes that identify Domino data structures that
are stored in canonical format to the ODS conversion routines.  The name of the
conversion code consists of an underscore followed by the name of the
structure.  For example, the conversion code for a WORD is \_WORD, and the code
for a CDHEADER is \_CDHEADER.


 


**Parameters :**



Input :  

name  -  Domino symbol for which an ODS conversion code is to be defined.  

  

num  -  Value of the ODS conversion code for this symbol.  

  

size  -  Size of the object in bytes.  

  




 


 **See Also :**


**[ODSReadMemory](ODSReadMemory.md)**


**[ODSLength](ODSLength.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[\_xxx (ODS Types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6624318DA38E8A885255F18007069DE)**



----------------------------------------------------------------------------------------------------------


 





