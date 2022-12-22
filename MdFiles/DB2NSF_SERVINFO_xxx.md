




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




**Initial Release 7.0**



**Symbolic Value : Database**



**DB2NSF\_SERVINFO\_xxx** **-** Flag for
NSFDB2GetServerInfo.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DB2NSF\_SERVINFO\_SERVER\_DEFAULT\_TYPE     -  Either of the
NULL terminated strings: "DB2" or "NSF", in LIMBCS.  

  

      DB2NSF\_SERVINFO\_NSFDB2\_CAPABLE    -  Determine if Domino capable of
serving NSFDB2 data. If the server can host NSFDB data, the buffer will contain
a "1". If the server is not properly set up to host NSFDB2 data, the
buffer will contain a "0". Maximum returned buffer size for this flag
is "sizeof(DWORD)".  

  

      DB2NSF\_SERVINFO\_DB2\_DATABASE\_NAME         -  DB2 database name.  

  




**Description :**



The type of
information for NSFDB2GetServerInfo to return.


 **See Also :**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**



----------------------------------------------------------------------------------------------------------


 





