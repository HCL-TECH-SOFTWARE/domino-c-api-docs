




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



**MIMEStreamRewind** **- rewind
the MIME stream to the beginning.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



int
LNPUBLIC **MIMEStreamRewind(**  

      MIMEHANDLE  hMIMEStream**);**



**Description :**



This
function, MIMEStreamRewind, rewinds a MIME stream to the beginning.  You must
specify as input the handle to the MIME stream.


 


MIMEStreamRewind
returns MIME\_STREAM\_SUCCESS if the buffer is rewound with no errors and
MIME\_STREAM\_IO if there are any err.


 


 


**Parameters :**



Input :  

hMIMEStream  -  a MIME stream handle  

  

  




Output :  

(routine)  -  returns MIME\_STREAM\_SUCCESS or MIME\_STREAM\_IO  

  

  




 **Sample Usage :**



int iReturn;


 


if ((iReturn =
MIMEStreamRewind(hMIMEStream)) == MIME\_STREAM\_IO) {


        goto exit;


}


 


 




----------------------------------------------------------------------------------------------------------


 





