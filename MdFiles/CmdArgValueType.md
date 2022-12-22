




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



**Data Type : HTML**



**CmdArgValueType** **-** Domino
Command Argument Value Types (CAVT)


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef enum


{


   
CAVT\_String     = 0,    /\* arg value is a pointer to a nul-terminated string \*/


   
CAVT\_Int        = 1,    /\* arg value is an int \*/


   
CAVT\_NoteId     = 2,    /\* arg value is a NOTEID \*/


   
CAVT\_UNID       = 3,    /\* arg value is an UNID \*/


   
CAVT\_StringList = 4     /\* arg value is a list of null-terminated strings \*/


 


} CmdArgValueType;


 


 


**Description :**



In the HTML
reference, there exist URL commands, and there are arguments associated with
those URL commands.This Data structure tells all the Domino Command Argument
Value Types 


 




----------------------------------------------------------------------------------------------------------


 





