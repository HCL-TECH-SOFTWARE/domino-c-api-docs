




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



**errortext** **-** Assign an
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

  

  

/\* "errortext" designates a user-displayed message (success, error,
warning).  

 This is translated, and may be shown to a user. There should be  

 online help for most of these messages. \*/  

  

#define errortext(code,text)  

  




 **Sample Usage :**


  

#define       MSG\_ADDIN\_NAME  (PKG\_ADDIN)  

    errortext(MSG\_ADDIN\_NAME,  "AddIn Name")  

  

#define       MSG\_ADDIN\_VERSION  (PKG\_ADDIN+1)  

    errortext(MSG\_ADDIN\_VERSION,  "Version 7.22+")  

  

#define       ERR\_EXAMPLE         (PKG\_ADDIN+2)  

    errortext(ERR\_EXAMPLE,      

              "AddIn: Error processing input Database %s")  

  

  




 **See Also :**


**[AddInFormatError](AddInFormatError.md)**


**[AddInLogError](AddInLogError.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[PKG\_xxx [ADDIN]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B540075E316)**


**[OSLoadString](OSLoadString.md)**



----------------------------------------------------------------------------------------------------------


 





