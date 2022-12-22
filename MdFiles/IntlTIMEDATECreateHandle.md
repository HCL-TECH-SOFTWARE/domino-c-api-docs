




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



**IntlTIMEDATECreateHandle** **- Create
handle for International TIMEDATE functionality.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **IntlTIMEDATECreateHandle(**  

      INTLTIMEDATEHANDLE \*hTimeDateHandle**);**



**Description :**



This
function is called to initialize the INTLTIMEDATEHANDLE..  This function  must
be the first function called when setting up to convert a TIMEDATE to text
using IntlTIMEDATEConvertToText.


 


 


**Parameters :**



Input :  

hTimeDateHandle  -  an INTLTIMEDATEHANDLE handle  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully created handle.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




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


 **See Also :**


**[IntlTIMEDATEConvertToText](IntlTIMEDATEConvertToText.md)**


**[IntlTIMEDATEDeleteHandle](IntlTIMEDATEDeleteHandle.md)**


**[IntlTIMEDATEGetValue](IntlTIMEDATEGetValue.md)**


**[INTLTIMEDATEHANDLE](INTLTIMEDATEHANDLE.md)**


**[IntlTIMEDATESetValue](IntlTIMEDATESetValue.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





