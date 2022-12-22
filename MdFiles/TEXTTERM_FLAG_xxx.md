




<!--
 /\* Font Definitions \*/
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



**Symbolic Value : Agents**



**TEXTTERM\_FLAG\_xxx** **-** Search
options for CDQUERYTEXTTERM.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      TEXTTERM\_FLAG\_RAW      -  String is a Domino full text
search query string.  

  

      TEXTTERM\_FLAG\_VERITY             -  String is stored in Verity search
engine format.  

  

      TEXTTERM\_FLAG\_AND      -  String is comma-separated list of words; AND
assumed.  

  

      TEXTTERM\_FLAG\_ACCRUE           -  String is comma-separated list of
words; ACCRUE assumed.  

  

      TEXTTERM\_FLAG\_NEAR    -  String is comma-separated list of words; NEAR
assumed.  

  

      TEXTTERM\_FLAG\_PLAINTEXT       -  Display this object as plain text.  

  




**Description :**



These option
flags may be specified in the dwFlags field of a CDQUERYTEXTTERM record.


 **See Also :**


**[CDQUERYTEXTTERM](CDQUERYTEXTTERM.md)**



----------------------------------------------------------------------------------------------------------


 





