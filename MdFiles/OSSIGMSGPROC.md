




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



**OSSIGMSGPROC** **-** Function
pointer template for Message signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include
<ossignal.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR OSSIGMSGPROC)(


   char far \* Message,  

   WORD       Type);


 


**Description :**



Definition
of a pointer to a function that will handle the Message signal.  The default
Message signal handler displays the text argument in a dialog box with
pushbuttons determined by the Type parameter.  The return value depends on the
type of display and user action;  please see the description of the appropriate
OSMESSAGETYPE\_xxx value for the possible return codes.  

  

This signal handler requires two parameters:  

  

    Message - Far pointer to a null-terminated message string to be displayed.  

  

    Type - How the message is to be displayed;  use one of the
OSMESSAGETYPE\_xxx Symbolic Values.


 **See Also :**


**[DesignRefresh](DesignRefresh.md)**


**[IXPostMessage](IXPostMessage.md)**


**[OSGetSignalHandler](OSGetSignalHandler.md)**


**[OSMESSAGETYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CFF00718D46)**


**[OSSetSignalHandler](OSSetSignalHandler.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





