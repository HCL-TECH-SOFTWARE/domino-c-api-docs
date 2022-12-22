




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



**MMSetSkipX** **- set
Conversion Controls 'skip X-Notes-Item headers' setting.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



void
LNPUBLIC **MMSetSkipX(**  

      CCHANDLE  hCC,  

      BOOL  bSkipX**);**



**Description :**



The
function  MMSetSkipX sets the Conversions Controls 'skip X-Notes-Item headers'
setting to the input value, bSkipX.  No checking is done for out of bounds
values.


 


**Parameters :**



Input :  

hCC  -  a handle to a Conversion Controls context from a previous call to
MMCreateConvControls.  

  

bSkipX  -  the value to use for the Conversion Controls 'skip X-Notes-Item
headers' setting.  

  




Output :  

(routine)  -  void  

  

  




 **Sample Usage :**


MMSetSkipX(hCC, TRUE);    /\*
if TRUE, don't export any headers named x-notes-item (default FALSE) \*/


 **See Also :**


**[MMGetSkipX](MMGetSkipX.md)**


**[CCHANDLE](CCHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





