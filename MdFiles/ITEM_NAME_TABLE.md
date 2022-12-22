




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




 


**Data Type : Item (Field)**



**ITEM\_NAME\_TABLE** **-** Header for
list of item names.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   USHORT Length; /\* total length of this buffer \*/  

   USHORT Items; /\* number of items in the table \*/  

/\* now comes an array of WORDS representing  

   the lengths of the item names. \*/  

/\* now comes the item names as packed text \*/  

} ITEM\_NAME\_TABLE;


 


**Description :**



This is the
header for lists of item names.  

  

This structure is followed by an array of WORD values containing the lengths,
in bytes, of the item names;  there is one WORD for each item name in the
table.  The array is followed, in turn, by the item names as packed data.


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**


**[READ\_MASK\_xxx](READ_MASK_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





