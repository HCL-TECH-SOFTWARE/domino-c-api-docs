




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



**stringtext** **-** Assign an
error code number to a text string.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



**Description :**



Assigns the
given error code to the given text string.  When language compiling, the macro
actually amounts to nothing more than a comment.  When resource compiling a
module (RC), the macro is used to map error code numbers to a corresponding
text string.


 


Prior to
Release 4.5, an alternative form was defined due to a compiler bug in MPW C. 
The compiler generated an error when a macro evaluated to nothing and is
followed by another #define.  

  

  

  

/\* "stringtext" designates translatable text fragments that need to
be  

 translated, but are not shown to the user as a "message" (error,  

 warning or otherwise). There should be no online help for these. \*/  

  

#define stringtext(code,text)  

  




 **See Also :**


**[errortext](errortext.md)**


**[helptext](helptext.md)**


**[apitext](apitext.md)**


**[debugtext](debugtext.md)**


**[internaltext](internaltext.md)**


**[blocktext](blocktext.md)**


**[semtext](semtext.md)**


**[limitedasciitext](limitedasciitext.md)**


**[donottranslatetext](donottranslatetext.md)**



----------------------------------------------------------------------------------------------------------


 





