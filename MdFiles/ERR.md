




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



**ERR** **- Mask off
flag bits from STATUS value.**


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



STATUS **ERR(**  

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

  

The bit flag STS\_REMOTE indicates that the error was detected on a remote Lotus
Domino Server, rather than on the local machine.  The bit flag STS\_DISPLAYED
indicates that some component of the system has already reported this error to
the user, so your program probably does not need to.  

  

The C API macro ERR() masks off these two bit flags, yielding an error code
with just the subsystem identifier and the subsystem-specific error code.  Use
the macro ERR() to mask off these bits before passing a STATUS error code to
OSLoadString, because these bits may prevent OSLoadString from interpreting the
code correctly.  

  

Note: This function is implemented as a macro:  

  

#define ERR(x) ((STATUS) (x & ERR\_MASK))


 


**Parameters :**



Input :  

x  -  STATUS error code returned from a C API function.  

  




Output :  

(routine)  -  STATUS error code with flag bits masked off.  

  

  




 **See Also :**


**[OSLoadString](OSLoadString.md)**


**[STATUS](STATUS.md)**


**[PKG](PKG.md)**


**[ERRNUM](ERRNUM.md)**


**[ERR\_MASK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A737A0088677AED78525623F005E6551)**



----------------------------------------------------------------------------------------------------------


 





