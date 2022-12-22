




<!--
 /\* Font Definitions \*/
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




 


**Function : Error Handling**



**ERRNUM** **- Error
code specific to the package portion of STATUS error code .**


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



STATUS **ERRNUM(**  

      STATUS  x**);**



**Description :**



The 16-bit
value of a STATUS error code consists of the following fields:


 


1 bit:     Flag
bit - status message has been displayed


1 bit:     Flag
bit - status message came from a remote machine (i.e., a server)


6 bits:   "Package"
code or partial package code


8 bits:   Status
value or partial package code plus status value


 


This macro
masks off the 2 flag bits and the 6-bit package code.  Note that newer package
codes may use more than 6 bits (leaving fewer than 8 bits for the status
value).  


 


Note: This
function is implemented as a macro:  

  

#define ERRNUM(x) ((STATUS) ((x) & ERRNUM\_MASK))


 


**Parameters :**



Input :  

x  -  STATUS error code returned from a C API function.  

  




Output :  

(routine)  -  STATUS error code with high order byte masked off.  

  

  




 **See Also :**


**[OSLoadString](OSLoadString.md)**


**[STATUS](STATUS.md)**


**[ERRNUM\_MASK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A9D4FF98CD99C3C98525623F005E9335)**


**[ERR](ERR.md)**


**[PKG](PKG.md)**



----------------------------------------------------------------------------------------------------------


 





