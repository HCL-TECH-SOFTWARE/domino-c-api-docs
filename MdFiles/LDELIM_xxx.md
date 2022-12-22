




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




 


**Symbolic Value : Field**



**LDELIM\_xxx** **-** Defines the
input separators used with multiple values in a document field.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LDELIM\_SPACE       -  When inputting multiple values,
separate them with a space.  

  

      LDELIM\_COMMA     -  When inputting multiple values, separate them with a
comma.  

  

      LDELIM\_SEMICOLON          -  When inputting multiple values, separate
them with a semicolon.  

  

      LDELIM\_NEWLINE   -  When inputting multiple values, separate them with a
newline.  

  

      LDELIM\_BLANKLINE            -  When inputting multiple values, separate
them with a blank line.  

  

      LD\_MASK     -  This may be used to mask out all bits defined for input
separators.  

  




**Description :**



Used to
define  how multiple values will be separated while they are being input. 
LDELIM\_xxx flags define the separators used while entering multiple values in a
field, while LDDELIM\_xxx flags define the separators that will be used when the
multiple values are displayed.


 **See Also :**


**[CDFIELD](CDFIELD.md)**


**[LDDELIM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DFAC93393AFD04878525620300636C6B)**



----------------------------------------------------------------------------------------------------------


 





