




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




**Initial Release 4.6**



**Symbolic Value : Resource Definition**



**donottranslatetext** **-** Assign an
error code number to a text string.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



**Description :**



Assigns the
given error code to the given text string.  When language compiling, the macro
actually amounts to nothing more than a comment.  When resource compiling a
module (RC), the macro is used to map error code numbers to a corresponding
text string.


 


/\*    "donottranslatetext"
designates text which must not be translated.  

      This text may be included in a resource file in order to facilitate  

      configuration changes, such as a string which controls program behavior.  

      Or it may be included in order to clearly indicate that the developer  

      intends for the text to remain untranslated.  

\*/


 


#define
donottranslatetext(code,text)


 **See Also :**


**[errortext](errortext.md)**


**[helptext](helptext.md)**


**[stringtext](stringtext.md)**


**[apitext](apitext.md)**


**[debugtext](debugtext.md)**


**[internaltext](internaltext.md)**


**[blocktext](blocktext.md)**


**[semtext](semtext.md)**


**[limitedasciitext](limitedasciitext.md)**



----------------------------------------------------------------------------------------------------------


 





