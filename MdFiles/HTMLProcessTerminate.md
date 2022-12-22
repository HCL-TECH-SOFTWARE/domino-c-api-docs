




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



**HTMLProcessTerminate** **- Releases
process wide resources.**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



void
LNPUBLIC **HTMLProcessTerminate(**void**);**



**Description :**



This
function releases process wide resources. Normally called once, when user process is
terminating. Can be called earlier, if no other HTML API operations are to be
performed. Undefined behavior if 


- called before
HTMLProcessInitialize()   


- called multiple
times.


If not called, process
will terminate with HTML API resources still allocated.


(Usually this is not a
problem)


 Threading: must be
called from one thread, no other concurrent HTML API calls.


 


 


**Parameters :**




Output :  

(routine)  -  void  

  

  




 **See Also :**


**[HTMLProcessInitialize](HTMLProcessInitialize.md)**



----------------------------------------------------------------------------------------------------------


 





