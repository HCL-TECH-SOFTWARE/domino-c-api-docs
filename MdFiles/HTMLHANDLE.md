




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



**HTMLHANDLE** **-** Converter
object handle


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef
MEMHANDLE HTMLHANDLE


 


**Description :**



A converter
object is used to access most of the HTML API's features.


 **Sample Usage :**


HTMLHANDLE cvtr;


rslt =
HTMLCreateConverter(&cvtr);


//use this converter to
do things you want to do


rslt =
HTMLDestroyConverter(cvtr)


 **See Also :**


**[HTMLCreateConverter](HTMLCreateConverter.md)**


**[HTMLDestroyConverter](HTMLDestroyConverter.md)**



----------------------------------------------------------------------------------------------------------


 





