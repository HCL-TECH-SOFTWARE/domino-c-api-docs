




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




 


**Symbolic Value : Views**



**VIEW\_CLASS\_xxx** **-** Upper four
bits of the BYTE ViewStyle member of the VIEW\_FORMAT\_HEADER structure.


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VIEW\_CLASS\_TABLE          -  Table class view.  

  

      VIEW\_CLASS\_CALENDAR   -  Calendar class view.  

  

      VIEW\_CLASS\_MASK            -  Bit mask for the VIEW\_CLASS\_xxx values.  

  




**Description :**



These
symbols specify the which of the upper four bits are set in the BYTE ViewStyle
member of the VIEW\_FORMAT\_HEADER structure.  These four bits specify the class
of a view (ie:  calendar or table view).  The lower four bits of the ViewStyle
member further define the style of a view style.


 **See Also :**


**[VIEW\_FORMAT\_HEADER](VIEW_FORMAT_HEADER.md)**



----------------------------------------------------------------------------------------------------------


 





