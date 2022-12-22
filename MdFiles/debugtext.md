




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




 


**Symbolic Value : Resource Definition**



**debugtext** **-** Assign an
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

  

  

  

/\* "debugtext" designates DEBUG-only messages. This is not to be  

 translated and never shown to a user. \*/  

  

#define debugtext(code,text)  

  




 **Sample Usage :**


#define ERR\_POOL\_FREE\_CHAIN                      PKG\_MISC+26  

    debugtext(ERR\_POOL\_FREE\_CHAIN,        "Invalid pool free chain")  

#define ERR\_LOCK\_POOL\_TWICE                      PKG\_MISC+27  

    debugtext(ERR\_LOCK\_POOL\_TWICE,        "Attempt to lock twice using
same pool lock")  

#define ERR\_TOO\_MANY\_LOCKS               PKG\_MISC+28  

    debugtext(ERR\_TOO\_MANY\_LOCKS,         "Too many locks on pool")


 **See Also :**


**[AddInFormatError](AddInFormatError.md)**


**[AddInLogError](AddInLogError.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[PKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/32ECB9B5852E43FE85256984004DEC2B)**


**[OSLoadString](OSLoadString.md)**



----------------------------------------------------------------------------------------------------------


 





