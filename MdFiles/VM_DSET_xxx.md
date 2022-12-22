




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




**Initial Release 4.0**



**Symbolic Value : Navigators**



**VM\_DSET\_xxx** **-** Option flags
for VIEWMAP\_DATASET\_RECORD.


**----------------------------------------------------------------------------------------------------------**



**#include <vmods.h>**


 **Symbolic Values :**      VM\_DSET\_SHOW\_GRID      -  Show the grid in design mode.  

  

      VM\_DSET\_SNAPTO\_GRID   -  Snap to grid.  

  

      VM\_DSET\_SAVE\_IMAGEMAP          -  Save a bitmap image of the navigator
for use by Web browsers.  

  

      VM\_DSET\_READING\_ORDER\_RTL             -  reading order  

  




**Description :**



These option
flags are stored in the Flags field of the VIEWMAP\_DATASET\_RECORD.


 


If the flag
VM\_DSET\_SAVE\_IMAGEMAP is set, a bitmap image of the navigator is generated and
stored.  When this navigator is accessed through a Domino server, the bitmap
image is displayed in the browser.


 **See Also :**


**[VIEWMAP\_DATASET\_RECORD](VIEWMAP_DATASET_RECORD.md)**



----------------------------------------------------------------------------------------------------------


 





