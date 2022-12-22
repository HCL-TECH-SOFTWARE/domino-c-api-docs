




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



**MMSetInbLineLen** **- set
Conversion Controls 'inbound line length' setting**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



void
LNPUBLIC **MMSetInbLineLen(**  

      CCHANDLE  hCC,  

      WORD  wInbLineLen**);**



**Description :**



The
function  MMSetInbLineLen sets the Conversions Controls 'inbound line length'
setting to the input value, wInbLineLen.  No checking is done for out of bounds
values.


 


**Parameters :**



Input :  

hCC  -  a handle to a Conversion Controls context from a previous call to
MMCreateConvControls.  

  

wInbLineLen  -  the value to use for the Conversion Controls 'inbound line
length' setting.  

  




Output :  

(routine)  -  void  

  

  




 **Sample Usage :**



MMSetInbLineLen(hCC,
75);     /\* if set, when converting MIME rich text parts (i.e., text/html) to
CD, justify using \*/


                              /\* 
this right margin.  (text/plain parts are never justified) (default is 75) \*


 


 **See Also :**


**[MMGetInbLineLen](MMGetInbLineLen.md)**


**[CCHANDLE](CCHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





