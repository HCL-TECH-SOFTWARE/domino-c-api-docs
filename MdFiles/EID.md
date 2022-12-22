




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




**Initial Release 4.0**



**Data Type : Extension Manager**



**EID** **-** Extension
manager function ID


**----------------------------------------------------------------------------------------------------------**



**#include
<extmgr.h>**



**Definition :**



typedef WORD EID


 


**Description :**



An EID
number is used to identify a C API function in the Extension Manager facility. 
This number is passed to EMRegister() to identify the function to be trapped,
and also to the extension manager callback function to identify which function
is being performed. See EM\_xxx for acceptable values for EIDs.  Incorrect
values will return an error from the function EMRegister().


 **See Also :**


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[EMRegister](EMRegister.md)**



----------------------------------------------------------------------------------------------------------


 





