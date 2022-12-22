




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



**Data Type : MIME**



**MIMEHANDLE** **-** an opaque
data type for using a MIME stream context that is created for reading and
writing MIME streams.


**----------------------------------------------------------------------------------------------------------**



**#include
<mime.h>**



**Definition :**



typedef void \*
MIMEHANDLE;


 


**Description :**



MIMEHANDLE
is a data type used to access a created MIME stream context.  See the
description for MIMEStreamOpen, MIMEStreamRead, MIMEStreamWrite, et al for more
information.


 **See Also :**


**[MIMEStreamClose](MIMEStreamClose.md)**


**[MIMEStreamOpen](MIMEStreamOpen.md)**


**[MIMEStreamRead](MIMEStreamRead.md)**


**[MIMEStreamWrite](MIMEStreamWrite.md)**



----------------------------------------------------------------------------------------------------------


 





