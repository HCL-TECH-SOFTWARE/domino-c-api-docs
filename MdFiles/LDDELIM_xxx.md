




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



**LDDELIM\_xxx** **-** Defines the
separators used to display multiple values in a document field.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      LDDELIM\_SPACE     -  When displaying multiple values,
separate them with a space.  

  

      LDDELIM\_COMMA   -  When displaying multiple values, separate them with a
comma.  

  

      LDDELIM\_SEMICOLON        -  When displaying multiple values, separate
them with a semicolon.  

  

      LDDELIM\_NEWLINE             -  When displaying multiple values, separate
them with a newline.  

  

      LDDELIM\_BLANKLINE          -  When displaying multiple values, separate
them with a blank line.  

  

      LDD\_MASK   -  This may be used to mask out all bits defined for display
separators.  

  




**Description :**



Used to
define  how multiple values will be separated while they are being displayed.  LDELIM\_xxx
flags define the separators used while entering multiple values in a field,
while LDDELIM\_xxx flags define the separators that will be used when the
multiple values are displayed.


 **See Also :**


**[CDFIELD](CDFIELD.md)**


**[LDELIM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2784EDD429BC15228525620300625C20)**



----------------------------------------------------------------------------------------------------------


 





