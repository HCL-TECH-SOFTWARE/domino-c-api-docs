




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




**Initial Release 6**



**Function : Miscellaneous**



**ERROR\_REMOTE** **- Indicate
whether the STS\_REMOTE bit is set.**


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



STATUS **ERROR\_REMOTE(**  

      STATUS  x**);**



**Description :**



Indicate
whether the STS\_REMOTE bit is set.


Note: This
function is implemented as a macro:


  

#define ERROR\_REMOTE(x)          ((x) & STS\_REMOTE)


 


**Parameters :**



Input :  

x  -  Status code.  

  




Output :  

(routine)  -  Return status from this call -- indicates whether the error
code's STS\_REMOTE bit is set.  

  

  




 **See Also :**


**[STATUS](STATUS.md)**


**[STS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4BDF0A3AB0A2A7F88525623F005A72AA)**



----------------------------------------------------------------------------------------------------------


 





