




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



**Function : Domino Upgrade Services**



**DUSStop** **- Notifies
the DUS that this is the end of this DUS session.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSStop(**  

      DHANDLE  hContext**);**



**Description :**



This
function notifies the DUS that the end of this session is over.  Memory
associated with the context handle, allocated in DUSStart(), should now be
freed.  


 


**Parameters :**



Input :  

hContext  -  handle to this DUS' specific context information.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 




----------------------------------------------------------------------------------------------------------


 





