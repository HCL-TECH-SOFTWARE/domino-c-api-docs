




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




**Initial Release 6.0.2**



**Function : Time**



**IntlTIMEDATEDeleteHandle** **- Delete
handle to International TIMEDATE functionality.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



void
LNPUBLIC **IntlTIMEDATEDeleteHandle(**  

      INTLTIMEDATEHANDLE  hTimeDateHandle**);**



**Description :**



Delete the
INTLTIMEDATEHANDLE allocated with IntlTIMEDATECreateHandle.


 


**Parameters :**



Input :  

hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to
IntlTIMEDATECreateHandle(..).  

  




Output :  

(routine)  -  None  

  

  




 **Sample Usage :**



INTLTIMEDATEHANDLE     hTimeDate;


 


if(error =
IntlTIMEDATECreateHandle( &hTimeDate ))


{


        printf
("Error: unable to convert TIMEDATE to text.\n");


      
TimeStringLen = 0;


        ItemText[TimeStringLen]
= '\0';


        break;


}


...


...


...


IntlTIMEDATEDeleteHandle(hTimeDate);


 **See Also :**


**[IntlTIMEDATECreateHandle](IntlTIMEDATECreateHandle.md)**


**[INTLTIMEDATEHANDLE](INTLTIMEDATEHANDLE.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





