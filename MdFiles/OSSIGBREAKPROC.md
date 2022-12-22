




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Signal Handler**



**OSSIGBREAKPROC** **-** Function
pointer template for Check Break signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include
<ossignal.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR OSSIGBREAKPROC)(void);


 


**Description :**



Definition
of a pointer to a function that will handle the Check Break signal.  The
default Check Break signal handler returns ERR\_CANCEL if the user has issued a
Break to interrupt network I/O, and NOERROR otherwise.  This signal handler
requires no parameters.


 **See Also :**


**[IXPostMessage](IXPostMessage.md)**


**[OSGetSignalHandler](OSGetSignalHandler.md)**


**[OSSetSignalHandler](OSSetSignalHandler.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





