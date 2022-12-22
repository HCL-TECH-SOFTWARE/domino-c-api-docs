




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




 


**Function : OS Environment Variables**



**OSGetEnvironmentSeqNo** **- Returns a
sequence number that represents the number of times any environment variable
has been changed.**


**----------------------------------------------------------------------------------------------------------**



**#include <osenv.h>**



WORD **OSGetEnvironmentSeqNo(**void**);**



**Description :**



This routine
returns a sequence number that represents the number of times an environment
variable has been changed. Returns 0 if none. This is useful to determine when
an environment variable has a new value.


 


**Parameters :**




Output :  

(routine)  -  Value of sequence number.  

  

  




 **Sample Usage :**


      /\*
Presume EnvironmentSeqNo external WORD variable. \*/ 


 


            WORD
NewEnvironmentSeqNo = OSGetEnvironmentSeqNo(); 


            if
(NewEnvironmentSeqNo != EnvironmentSeqNo) 


            {



                        EnvironmentSeqNo
= NewEnvironmentSeqNo; 


                        /\*
Perform environment variable change logic. \*/ 


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





