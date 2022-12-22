




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



**MIMEStreamPutLine** **- Write a
line to a MIME stream.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



int
LNPUBLIC **MIMEStreamPutLine(**  

      char \*pszLine,  

      MIMEHANDLE  hMIMEStream**);**



**Description :**



This
function MIMEStreamPutLine writes a line of data to a MIME stream.  You must
specify as input a pointer to a line of NUL terminated text and the handle to
the MIME stream.


 


MIMEStreamPutLine
appends the input line to the MIME stream and then appends carriage return,
line feed (CRLF) to the MIME stream.  If the data is written sucessfully to the
MIME stream, MIMEStreamPutLine returns MIME\_STREAM\_SUCCESS.  If it detects any
errors while writing to the MIME stream, it returns MIME\_STREAM\_IO.  Note that
the MIME stream must be opened for write by specifying the
MIME\_STREAM\_OPEN\_WRITE flag on the MIMEStreamOpen call.


 


 


**Parameters :**



Input :  

pszLine  -  A pointer to a line of NULL terminated text.  

  

hMIMEStream  -  A handle to the MIME stream.  

  




Output :  

(routine)  -  Return status from this call.  

     MIME\_STREAM\_IO - returned if there are errors writing to the stream or if
the stream was not opened for writing.  

  

  

  




 **Sample Usage :**


int iReturn;


 


if ((iReturn =
MIMEStreamPutLine(pszLine, hMIMEStream)) == MIME\_STREAM\_IO) {


        goto exit;


}


 


 **See Also :**


**[MIMEStreamGetLine](MIMEStreamGetLine.md)**


**[MIMEStreamItemize](MIMEStreamItemize.md)**


**[MIME\_STREAM\_xxx](MIME_STREAM_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





