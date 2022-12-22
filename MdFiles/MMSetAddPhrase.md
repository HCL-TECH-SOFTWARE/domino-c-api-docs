




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



**MMSetAddPhrase** **- set
Conversion Controls 'add phrase' setting.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



void
LNPUBLIC **MMSetAddPhrase(**  

      CCHANDLE  hCC,  

      WORD  wAddPhrase**);**



**Description :**



The
function  MMSetAddPhrase sets the Conversions Controls 'add phrase' setting to
the input value, wAddPhrase.  No checking is done for out of bounds values.


 


 


**Parameters :**



Input :  

hCC  -  a handle to a Conversion Controls context from a previous call to
MMCreateConvControls.  

  

wAddPhrase  -  the value to use for the Conversion Controls 'add phrase'
setting.  

  




Output :  

(routine)  -  void  

  

  




 **Sample Usage :**



MMSetAddPhrase(hCC, 0);               /\*      0/1
- no phrase added or removed,


                                             2  
- add abbreviated DN,


                                             3  
- add alt name if it exists else DN,


                                             4  
- Remove all phrases and comments (default 0) \*/


 


 **See Also :**


**[MMGetAddPhrase](MMGetAddPhrase.md)**


**[CCHANDLE](CCHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





