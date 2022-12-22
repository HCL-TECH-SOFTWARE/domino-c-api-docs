




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



**MIMEStreamWrite** **- put a
buffer to a MIME stream.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



int
LNPUBLIC **MIMEStreamWrite(**  

      unsigned char \*pchData,  

      unsigned int  uiDataLen,  

      MIMEHANDLE  hMIMEStream**);**



**Description :**



This
function, MIMEStreamWrite, writes a buffer to the input MIME stream.  You must
specify as input a pointer to a buffer, an unsigned int with the number of
bytes to write, and the handle to the MIME stream.


 


MIMEStreamWrite
returns MIME\_STREAM\_SUCCESS if the buffer is written with no errors and
MIME\_STREAM\_IO if there are any errors when it attempts to write to the MIME
stream.


 


 


**Parameters :**



Input :  

pchData  -  a pointer to a write buffer.  

  

uiDataLen  -  the number of bytes to write from the write buffer.  

  

hMIMEStream  -  a MIME stream handle  

  




Output :  

(routine)  -  returns MIME\_STREAM\_SUCCESS or MIME\_STREAM\_IO  

  

  




 **Sample Usage :**



int iReturn;


char
pchBuf[MAX\_BUFFER\_SIZE];


 


if ((iReturn =
MIMEStreamWrite(pchBuf, MAX\_BUFFER\_SIZE, hMIMEStream)) == MIME\_STREAM\_IO) {


        goto exit;


}


 


 **See Also :**


**[MIMEHANDLE](MIMEHANDLE.md)**


**[MIMEStreamRead](MIMEStreamRead.md)**



----------------------------------------------------------------------------------------------------------


 





