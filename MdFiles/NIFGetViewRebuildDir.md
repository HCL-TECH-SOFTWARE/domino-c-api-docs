




<!--
 /\* Font Definitions \*/
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




 


**Function : Dir; Views**



**NIFGetViewRebuildDir** **- Return a
view directory name.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



BOOL **NIFGetViewRebuildDir(**  

      char \*szTempDir,  

      WORD  wBufLen**);**



**Description :**



Validate
that a view directory exists and if so return its name.


 


**Parameters :**



Input :  

  

wBufLen  -  Maximum lenth of the buffer  

  




Output :  

(routine)  -  view directory name  

  

  

szTempDir  -  Place holder for view directory  

  




 **Sample Usage :**



char
szTempDir[MAXPATH]
= { 0 };


 


NIFGetViewRebuildDir(szTempDir,
sizeof(szTempDir)-1)



 


/\*
Processing using szTempDir \*/                                   


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





