




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




**Initial Release 8.5**



**Symbolic Value : archiving service**



**ARCHSVC\_LOG\_xxx** **-** Controls
tracing/debug output These should be "FLAGS" so that we can get
"just enough" output.


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**


 **Symbolic Values :**      ARCHSVC\_LOG\_ERROR     -  Enables tracing on all error
returns so that callers can see the origin of a low level API error.  

  

      ARCHSVC\_LOG\_DEBUG     -  Enables the debug dump of key data structures
during the export/import process.  

  

      ARCHSVC\_LOG\_ENTRYEXIT          -  Logs the entry/exit of all archiving
service functions along with argument and return values. This will help support
pinpoint the cause of any errors that may occur.  

  




**Description :**



The
archiving functions have the ability to output trace information to the file
specified in the DEBUG\_OUTFILE notes ini setting. Tracing is enabled via the
LOG\_ARCHSVC notes ini variable.


 




----------------------------------------------------------------------------------------------------------


 





