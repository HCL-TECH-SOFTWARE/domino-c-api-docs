




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




 


**Symbolic Value : Time**



**TDFMT\_xxx** **-** TFMT -
Date.  Specifies the Date format for character time/date strings.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**


 **Symbolic Values :**      TDFMT\_FULL           -  Date format is: year, month, and day  

  

      TDFMT\_CPARTIAL   -  Date format is: month and day, year if not this year  

  

      TDFMT\_PARTIAL     -  Date format is: month and day  

  

      TDFMT\_DPARTIAL   -  Date format is: year and month  

  

      TDFMT\_FULL4         -  Date format is: year (4-digit ), month, and day  

  

      TDFMT\_CPARTIAL4            -  Date format is: month and day, year (4-digit
) if not this year  

  

      TDFMT\_DPARTIAL4            -  Date format is: year (4-digit ) and month  

  




**Description :**



These
definitions specify the format for character time/date strings. Use these
definitions when you set up the TFMT structure that controls the time/date
format.


 **See Also :**


**[TFMT](TFMT.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTextToTIMEDATEPAIR](ConvertTextToTIMEDATEPAIR.md)**



----------------------------------------------------------------------------------------------------------


 





