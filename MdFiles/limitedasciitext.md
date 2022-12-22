




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




 


**Symbolic Value : Resource Definition**



**limitedasciitext** **-** Assign an
error code number to a text string.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



**Description :**



Assigns the
given error code to the given text string.  When language compiling, the macro
actually amounts to nothing more than a comment.  When resource compiling a
module (RC), the macro is used to map error code numbers to a corresponding
text string.


 


/\*    "limitedasciitext"
designates text which is constrained to a limited  

      subset of a platform character set.  One use of this macro is for strings
used as  

      part of Internet protocols which do not allow for non-platform character
text.  

      The exact limitations will vary with usage, but will usually be  

      restricted to 7-bit character, excluding '\0'.  These strings MAY be  

      translated to other languages, but must keep within the limited text  

      characters allowed.  For example, translation into French is permitted,  

      but no accented characters may be used.  

\*/


  

#define limitedasciitext(code,text)


 **See Also :**


**[errortext](errortext.md)**


**[helptext](helptext.md)**


**[stringtext](stringtext.md)**


**[apitext](apitext.md)**


**[debugtext](debugtext.md)**


**[internaltext](internaltext.md)**


**[blocktext](blocktext.md)**


**[semtext](semtext.md)**


**[donottranslatetext](donottranslatetext.md)**



----------------------------------------------------------------------------------------------------------


 





