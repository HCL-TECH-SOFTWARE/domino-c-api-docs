




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




**Initial Release 5.0**



**Symbolic Value : Character
Manipulation**



**NLS\_xxx (TRANSLATE)** **-** Control
flags used by the function NLS\_translate.


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**


 **Symbolic Values :**      NLS\_NONULLTERMINATE   -  Does not add a NULL to the end of
the translated result.  

  

      NLS\_NULLTERMINATE        -  Adds a NULL to the end of the translated
result.  

  

      NLS\_STRIPUNKNOWN        -  Strips unknown characters.  

  

      NLS\_TARGETISLMBCS       -  Converts target string to LMBCS.  

  

      NLS\_SOURCEISLMBCS       -  Converts source string from LMBCS.  

  

      NLS\_TARGETISUNICODE   -  Converts target string to UNICODE.  

  

      NLS\_SOURCEISUNICODE   -  Converts source string from UNICODE.  

  

      NLS\_TARGETISPLATFORM             -  Converts target string to the
encoding used by the host OS.  

  

      NLS\_SOURCEISPLATFORM            -  Converts source string from the
encoding used by the host OS.  

  




**Description :**



Control
flags used by the function NLS\_translate to govern how the translation is
performed.


 **See Also :**


**[ACLGetHistory](ACLGetHistory.md)**


**[NLS\_translate](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/155C97DCEEF0C3EE8525662800461D66)**



----------------------------------------------------------------------------------------------------------


 





