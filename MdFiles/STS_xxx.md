




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




 


**Symbolic Value : Error Handling**



**STS\_xxx** **-** Error code
status flags.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**


 **Symbolic Values :**      STS\_DISPLAYED     -  Error has already been displayed.  

  

      STS\_REMOTE         -  Error came from remote machine.  

  




**Description :**



The 16-bit
value of a STATUS error code consists of two bit flags, a subsystem code, and
an error code specific to the subsystem.The top two bits of the error code are
reserved for the bit flags and indicate an error code status ; four values can
be encoded of which two are currently used.


 **See Also :**


**[ERR](ERR.md)**


**[ERR\_MASK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A737A0088677AED78525623F005E6551)**



----------------------------------------------------------------------------------------------------------


 





