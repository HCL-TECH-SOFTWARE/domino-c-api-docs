




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




**Initial Release 7.0.2**



**Function : MIME**



**MMGetMessageContentEncoding** **- Get
Conversion Controls 'message content encoding' setting.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



WORD
LNPUBLIC **MMGetMessageContentEncoding(**  

      CCHANDLE  hCC**);**



**Description :**



The
function  MMGetMessageContentEncoding returns the current Conversions Controls
'message content encoding' setting.


 


**Parameters :**



Input :  

hCC  -  a handle to a Conversion Controls context from a previous call to
MMCreateConvControls.  

  




Output :  

(routine)  -  the WORD value for the current message content encoding setting:  

                  0 - text/plain (w/o images & attachments)   

                  1 - text/plain (w/images & attachments)   

                  2 - text/html (w/images & attachments)  

                  3 - multipart/alternative: text/plain & text/html
(w/images & attachments)  

  

  




 **Sample Usage :**



WORD
wMessageContentEncoding;


 


wMessageContentEncoding
= MMGetMessageContentEncoding(hCC);


 


 **See Also :**


**[CCHANDLE](CCHANDLE.md)**


**[MMSetMessageContentEncoding](MMSetMessageContentEncoding.md)**



----------------------------------------------------------------------------------------------------------


 





