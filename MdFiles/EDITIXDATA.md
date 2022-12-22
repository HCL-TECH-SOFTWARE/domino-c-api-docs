




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




 


**Data Type : Add-In DLL**



**EDITIXDATA** **-** Contains
import/export information.


**----------------------------------------------------------------------------------------------------------**



**#include
<addinmen.h>**



**Definition :**



typedef struct {  

   EDITIMPORTDATA Import;  

   EDITEXPORTDATA Export;  

   char           CaretFieldName[34];  

   WORD           CaretFieldType;  

} EDITIXDATA;


 


**Description :**



This
structure provides import/export data as well as the name of the field and type
of field of the current cursor position.  Menu add-in functions receive this
information when processing the NAMM\_COMMAND message from Notes.  

  

The CaretFieldName member of the EDITIXDATA structure gives the name of the
field containing the cursor when the menu item was chosen.  The CaretFieldType
member of the EDITIXDATA structure gives the field type of the field containing
the cursor when the Notes user selected the menu add-in's item from the Tools
menu.  See FIELD\_TYPE\_xxx for the values for CaretFieldType.


 **See Also :**


**[NAM\_CONTEXT\_DATA](NAM_CONTEXT_DATA.md)**


**[EDITIMPORTDATA](EDITIMPORTDATA.md)**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[FIELD\_TYPE\_xxx](FIELD_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





