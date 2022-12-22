




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




 


**Symbolic Value : Limits**



**MAXONESEGSIZE** **-** Maximum
single-segment memory object size.


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



**Description :**



Defined for
OSMem for those platforms with segmentation, allotting space for overhead. 


  

 Note: Beginning in V3.2, MAXONESEGSIZE is defined to be the MINIMUM of the
required MAXONESEGSIZE on all platforms, because, for example, if a server
allocates an object that is MAXONESEGSIZE and then sends it to a client, the
client's definition of MAXONESEGSIZE must be the same as the server's.


 **See Also :**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemRealloc](OSMemRealloc.md)**



----------------------------------------------------------------------------------------------------------


 





