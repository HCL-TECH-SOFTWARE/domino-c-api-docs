




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : HTML**



**HTMLProcessInitialize** **-
Initializes the HTML API process-wide resources.**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLProcessInitialize(**void**);**



**Description :**



This function
initializes the HTML API process-wide resources. Normally called once, when
user process is initializing.Calling this is Optional -- if not called, the
first call to HTMLCreateConverter will do initialization.Multiple calls are OK
-- they do not "nest" (i.e. multiple calls do not pair with HTMLProcessTerminate().)
Calling this after a call to HTMLProcessTerminate() results in undefined
behavior.


Threading:
can be called from multiple threads concurrently  with HTMLCreateConverter()


 


**Parameters :**




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  




 **See Also :**


**[HTMLProcessTerminate](HTMLProcessTerminate.md)**



----------------------------------------------------------------------------------------------------------


 





