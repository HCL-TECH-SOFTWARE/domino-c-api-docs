




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




**Initial Release 8.5.2**



**Function : OOO**



**OOOSetAwayPeriod** **- This
function validates and sets the time parameters that control OOO.** 


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOSetAwayPeriod(**  

      OOOCTXPTR \*pOOOContext,  

      TIMEDATE  tdStartAway,  

      TIMEDATE  tdEndAway**);**



**Description :**



This
function validates and sets the time parameters that control OOO.  This
information is required for enabling the OOO. 


      If you
want turn on OOO functionality for a given period of time the sequence of calls
needed is: **OOOStartOperation**, **OOOSetAwayPeriod**, **OOOEnable**,
**OOOEndOperation**.  


 


        When
you need to enable OOO (i.e. call it with bState flag set to TRUE) you should
call **OOOSetAwayPeriod** prior to calling **OOOEnable.** 



      If you
need to change the length of the away period after OOO has already been
enabled, the sequence of calls needed to perform this action is  **OOOStartOperation**,
**OOOSetAwayPeriod**, **OOOEndOperation**.  


 


      If the
Domino server is configured to run an OOO agent, it can only be turned on for
full days, the time portion of the date parameter will not be used.


 


**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call  

  

tdStartAway  -  This is date and time when Out of office will begin.  

  

tdEndAway  -  This is date and time when Out of office will end.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

NOERROR - Successfully performed this operation  

This function can return Domino errors.  

OOO specific errors:  

ERR\_OOO\_MISSING\_PARAM - One or more mandatory parameters were not specified  

ERR\_OOO\_MISSING\_MAILFILE - Mailfile information is not specified  

  

  




 **See Also :**


**[OOOGetAwayPeriod](OOOGetAwayPeriod.md)**



----------------------------------------------------------------------------------------------------------


 





