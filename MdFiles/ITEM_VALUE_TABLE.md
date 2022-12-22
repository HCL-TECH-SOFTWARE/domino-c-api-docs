




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



**ITEM\_VALUE\_TABLE** **-** Header for
lists of data values


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   USHORT Length; /\* total length of this buffer \*/  

   USHORT Items;  /\* number of items in the table \*/  

/\* now comes an array of WORDS representing  

   the lengths of the item values. \*/  

/\* now comes the item values as packed bytes \*/  

} ITEM\_VALUE\_TABLE;


 


**Description :**



This is the
header for lists of values with a variable number of entries having variable
sizes.  The fields in the structure are:  

  

    Length - Total length of the block of memory.  

  

    Items - Number of items in the table.  

  

This structure is followed by an array of WORD values containing the lengths,
in bytes, of the data items;  there is one WORD for each item in the table. 
The data length table is followed, in turn, by a packed sequence of item
values.  Each item value includes the item's datatype. The item's datatype is
stored in the first USHORT of each item value.


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**


**[READ\_MASK\_xxx](READ_MASK_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





