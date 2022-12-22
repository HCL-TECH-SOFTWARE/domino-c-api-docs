




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




 


**Function : Miscellaneous**



**RAWBLK** **- Return
the "raw" error status code value.**


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



STATUS **RAWBLK(**  

      STATUS  x**);**



**Description :**



Return the
"raw" error status code value, with the status code flags removed, as
a value of type STATUS.


 


Note: This
function is implemented as a macro:


  

#define RAWBLK(x) ((STATUS) ((x)&~(STS\_DISPLAYED|STS\_REMOTE)))


 


**Parameters :**



Input :  

x  -  Error status code.  

  




Output :  

(routine)  -  "Raw" error status code value, with the status code
flags removed.  

  

  




 **See Also :**


**[NOBLK](NOBLK.md)**


**[STATUS](STATUS.md)**


**[STS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4BDF0A3AB0A2A7F88525623F005A72AA)**



----------------------------------------------------------------------------------------------------------


 





