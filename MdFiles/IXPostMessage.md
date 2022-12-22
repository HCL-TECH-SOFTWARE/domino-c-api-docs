




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




 


**Function : Signal Handler**



**IXPostMessage** **- Place a
text string in the Workstation's Status Bar.**


**----------------------------------------------------------------------------------------------------------**



**#include <ixport.h>**



void **IXPostMessage(**  

      char far \*str**);**



**Description :**



This MACRO
provides a simple wrapper for OSGetSignalHandler, that allows you to place/post
a null-terminated string in the message/status area of the Status Bar of the
Lotus Notes workstation application.  This function can be used to provide OS
independent status updates to the user.  This function should only be used in a
GUI environment.    

  

#define
IXPostMessage(str) \  

(OSGetSignalHandler(OS\_SIGNAL\_MESSAGE) ? \  

(\*(OSSIGMSGPROC)OSGetSignalHandler(OS\_SIGNAL\_MESSAGE))(str,OSMESSAGETYPE\_POST\_NOSERVER)\


 : NOERROR)


 


Note: You
may wish to provide a suitable delay in your code during which, the user is
able to absorb the contents of the message.  This is because the Workstation
application may update the Status Bar as soon as your program relinquishes
control.  The usual cause is a mail delivery notification message or some
network broadcast.


 


**Parameters :**



Input :  

str  -  A pointer to a null-terminated string containing the message you would
like to display.  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**


/\* Open the Export file
\*/  

IXPostMessage("Begin writing the Export file.");  

for (count = 0; count < 1048576; count++) /\* Poor night's sleep \*/;  

   hExpFile = OpenFile( FileName, &ExpOfStruct, OF\_CREATE);


 **See Also :**


**[OSGetSignalHandler](OSGetSignalHandler.md)**



----------------------------------------------------------------------------------------------------------


 





