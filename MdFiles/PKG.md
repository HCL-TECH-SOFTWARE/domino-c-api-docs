




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



**PKG** **- Return
the Domino package code.**


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



STATUS **PKG(**  

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


 


The package
code identifies which Notes component generated the status code.  The PKG macro
masks off the 2 flag bits and the 8 lowest bits, leaving only the package
code.  This function is useful only with package codes that use the designated
6 bits of the status code.  Newer package codes may use more than 6 bits
(leaving fewer than 8 bits for the status value).  This function will not
return the correct results for these newer package codes.


 


Note: This
function is implemented as a macro:  

  

#define PKG(x) ((STATUS) ((x) & PKG\_MASK))


 


**Parameters :**



Input :  

x  -  Notes status code.  

  




Output :  

(routine)  -  Package code from a Domino STATUS value.  

  

  




 **See Also :**


**[STATUS](STATUS.md)**


**[STS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4BDF0A3AB0A2A7F88525623F005A72AA)**


**[ERR](ERR.md)**


**[ERRNUM](ERRNUM.md)**


**[PKG\_MASK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4ECCFDFBEB01D0C68525623F005E7E71)**



----------------------------------------------------------------------------------------------------------


 





