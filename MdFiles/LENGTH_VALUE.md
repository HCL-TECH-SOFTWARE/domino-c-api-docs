




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



**Data Type : Rich Text**



**LENGTH\_VALUE** **-** Structure
used to store a length to disk. 


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct  

   {  

   WORD              Flags;  

   ALIGNED\_NUMBER    Length;  

   BYTE              Units;  

   BYTE              Reserved; /\* reserved for future use \*/  

   } LENGTH\_VALUE;


 


 


**Description :**



This record
contains information for storing a length to disk.  The fields in this record
are:


 


Flags                See
CDLENGTH\_FLAGS\_xxx. 


Length              Length
of the record.


Units                See
CDLENGTH\_UNITS\_xxx. 


Reserved          Reserved
for future use.


 **See Also :**


**[CDBACKGROUNDPROPERTIES](CDBACKGROUNDPROPERTIES.md)**


**[CDBOXSIZE](CDBOXSIZE.md)**


**[CDLENGTH\_FLAGS\_xxx](CDLENGTH_FLAGS_xxx.md)**


**[CDLENGTH\_UNITS\_xxx](CDLENGTH_UNITS_xxx.md)**


**[CDPOSITIONING](CDPOSITIONING.md)**



----------------------------------------------------------------------------------------------------------


 





