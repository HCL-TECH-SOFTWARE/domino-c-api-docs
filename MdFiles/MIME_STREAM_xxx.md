




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




**Initial Release 7.0.2**



**Symbolic Value : MIME**



**MIME\_STREAM\_xxx** **-** flags and
return values used by MIMEStreamxxx APIs.


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**


 **Symbolic Values :**      MIME\_STREAM\_OPEN\_READ         -  for the input note, open a
MIME stream for reading.  

  

      MIME\_STREAM\_OPEN\_WRITE       -  for the input note, open a MIME stream
for writing.  

  

      MIME\_STREAM\_MIME\_INCLUDE\_HEADERS           -  Include MIME Headers.  

  

      MIME\_STREAM\_RFC2822\_INCLUDE\_HEADERS     -  Include RFC822 Headers  

  

      MIME\_STREAM\_INCLUDE\_HEADERS         -  for the input note, include the
part headers in the MIME stream.  

  

      MIME\_STREAM\_SUCCESS              -  return value: successful MIME stream
I/O.  

  

      MIME\_STREAM\_EOS           -  return value: End Of Stream -- no more data
in the MIME stream.  

  

      MIME\_STREAM\_IO   -  return value: I/O error; e.g.., a write to a
read-only MIME stream.  

  

      MIME\_STREAM\_ITEMIZE\_HEADERS          -  flag to MIMEStreamItemize: create
items for part headers (only for initial RFC822 headers, not MIME part headers)  

  

      MIME\_STREAM\_ITEMIZE\_BODY     -  flag to MIMEStreamItemize: create items
for part bodies.  

  

      MIME\_STREAM\_ITEMIZE\_FULL      -  OR'd MIME\_STREAM\_ITEMIZE\_HEADERS and
MIME\_STREAM\_ITEMIZE\_BODY flags.  

  

      MIME\_STREAM\_NO\_DELETE\_ATTACHMENTS       -  flag to MIMEStreamItemize:
don't delete attachment during itemization.  

  




**Description :**



flags and
return values used by MIMEStreamxxx APIs.


 **See Also :**


**[MIMEStreamClose](MIMEStreamClose.md)**


**[MIMEStreamGetLine](MIMEStreamGetLine.md)**


**[MIMEStreamItemize](MIMEStreamItemize.md)**


**[MIMEStreamOpen](MIMEStreamOpen.md)**


**[MIMEStreamPutLine](MIMEStreamPutLine.md)**



----------------------------------------------------------------------------------------------------------


 





