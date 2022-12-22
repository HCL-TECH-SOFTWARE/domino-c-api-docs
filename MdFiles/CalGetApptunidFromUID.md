




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




**Initial Release 9.0.1**



**Function : iCalendar**



**CalGetApptunidFromUID** **- Returns
an Apptunid value that corresponds to a UID**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalGetApptunidFromUID(**  

      const char\*pszUID,  

      char\*pszApptunid,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



This is a convenience
method that returns an Apptunid value that corresponds to a UID.


The
pszApptunid buffer MUST be allocated by the caller and a minimum of 33 bytes
long. This method populates the buffer with 32 bytes and a NULL terminator


 


**Parameters :**



Input :  

pszUID  -  UID of the icalendar entry  

  

dwFlags  -  Must be 0  

  

pCtx  -  Must be NULL  

  




Output :  

(routine)  -  Status of the function  

  

  

pszApptunid  -  Allocated buffer for return value  

  




 




----------------------------------------------------------------------------------------------------------


 





