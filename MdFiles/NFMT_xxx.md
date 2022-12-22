




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



**NFMT\_xxx** **-** NFMT -
Format.  Specifies the format for character number strings.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**


 **Symbolic Values :**      NFMT\_GENERAL     -  Only the significant digits in a number
will be displayed; leading zeroes and trailing zeroes will be stripped.  

  

      NFMT\_FIXED           -  The number displayed will contain to the right of
the decimal point the number of digits specified in the NFMT->Digits
structure member. The number will be either truncated or padded with zeroes, as
appropriate.  

  

      NFMT\_SCIENTIFIC   -  The number will be displayed in scientific notation.  

  

      NFMT\_CURRENCY   -  The appropriate currency symbol will be displayed with
the number.  

  




**Description :**



These
definitions specify the format for character number strings. Use these definitions
when you set up the NFMT structure that controls the number format.


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


 





