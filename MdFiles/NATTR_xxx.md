




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




 


**Symbolic Value : Number**



**NATTR\_xxx** **-** NFMT -
Attributes.  Specifies attributes for character number strings.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**


 **Symbolic Values :**      NATTR\_PUNCTUATED        -  The number will be punctuated by
the appropriate separator character.  

  

      NATTR\_PARENS     -  Negative numbers will be displayed in parentheses,
rather than being preceded by a minus sign.  

  

      NATTR\_PERCENT   -  The number entered will be interpreted as a
percentage, and will be converted to its decimal equivalent by moving the
decimal point two places to the left.  

  

      NATTR\_VARYING    -  Numbers can have a varying number of decimal places
(applies to Decimal & Percent only).  

  




**Description :**



These
definitions specify the format for character number strings. Use these
definitions when you set up the NFMT structure that controls the number format.


 **Sample Usage :**


  

/\*  

 \*  Set up Number format  

 \*/    

  

NFMT NumberFormat;    

  

NumberFormat.Digits     = 6;  

NumberFormat.Format     = NFMT\_GENERAL;  

NumberFormat.Attributes = NATTR\_PUNCTUATED;  

NumberFormat.Unused     = 0;  

  

  

  




 **See Also :**


**[NFMT](NFMT.md)**



----------------------------------------------------------------------------------------------------------


 





