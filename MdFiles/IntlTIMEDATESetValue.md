




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



**IntlTIMEDATESetValue** **- Set
INTL\_TIMEDATE\_PROPERTY value.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **IntlTIMEDATESetValue(**  

      INTLTIMEDATEHANDLE  hTimeDateHandle,  

      INTL\_TIMEDATE\_PROPERTY  prop,  

      void \*propValue**);**



**Description :**



Set the
property value to either AMStringProperty or PMStringProperty defined in
INTL\_TIMEDATE\_PROPERTY.


 


**Parameters :**



Input :  

hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to
IntlTIMEDATECreateHandle.  

  

prop  -  either set the AMStringProperty or the PMStringProperty value.  

  

propValue  -  value set for either the AMStringProperty or the PMStringProperty  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully set value  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **Sample Usage :**



char                          UserDefinedString[]=
"Intl Setting PM";


INTL\_TIMEDATE\_PROPERTY propValue;


 


propValue =
PMStringProperty;


if(error =
IntlTIMEDATESetValue(hTimeDate, propValue, UserDefinedString))


{


        IntlTIMEDATEDeleteHandle(
hTimeDate );


        printf
("Error: unable to convert TIMEDATE to text.\n");


      
TimeStringLen = 0;


        ItemText[TimeStringLen]
= '\0';


        break;


}


 **See Also :**


**[IntlTIMEDATECreateHandle](IntlTIMEDATECreateHandle.md)**


**[IntlTIMEDATEGetValue](IntlTIMEDATEGetValue.md)**


**[INTL\_TIMEDATE\_PROPERTY](INTL_TIMEDATE_PROPERTY.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





