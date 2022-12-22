




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




**Initial Release 4.0**



**Data Type : Navigators**



**VIEWMAP\_HEADER\_RECORD** **-** Header CD
record for Navigator layout.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

   WORD Version; /\* (see VIEWMAP\_VERSION) \*/  

   WORD NameLen;  

} VIEWMAP\_HEADER\_RECORD;


 


**Description :**



The
VIEWMAP\_HEADER\_RECORD is the first record in an item of type
TYPE\_VIEWMAP\_LAYOUT, the graphical layout of a Navigator.  The fields in this
structure are:


 


Header             Identfies
this record as a VIEWMAP\_HEADER\_RECORD.


Version             Version
number of Navigator record formats.  Use VIEWMAP\_VERSION value.


NameLen          Reserved
for future use.   Set to 0. 


 **See Also :**


**[VIEWMAP\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E13066D4308549648525626100700530)**



----------------------------------------------------------------------------------------------------------


 





