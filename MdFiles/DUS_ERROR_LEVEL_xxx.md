




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



**Symbolic Value : Domino Upgrade
Services**



**DUS\_ERROR\_LEVEL\_xxx** **-** For extended
error processing. Used in pErrorLevel param with DUSExtendedErrorText.


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**


 **Symbolic Values :**      DUS\_ERROR\_LEVEL\_INFO             -  DUS application
declaring an informational error only.  

  

      DUS\_ERROR\_LEVEL\_WARNING     -  DUS application declaring a warning
message only.  

  

      DUS\_ERROR\_LEVEL\_ERROR         -  DUS application declaring a fatal error
which will signify the DUS framework to shutdown the DUS application
gracefully.  

  

      DUS\_ERROR\_NO\_DISPLAY             -  Use this flag if the error should not
be displayed.  

  




 **See Also :**


**[DUSExtendedErrorText](DUSExtendedErrorText.md)**



----------------------------------------------------------------------------------------------------------


 





