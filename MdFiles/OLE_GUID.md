




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




**Initial Release 4.1**



**Data Type : OLE**



**OLE\_GUID** **-** On-disk
structure of an OLE GUID.


**----------------------------------------------------------------------------------------------------------**



**#include
<oleods.h>**



**Definition :**



typedef struct {  

   DWORD Data1;  

   WORD  Data2;  

   WORD  Data3;  

   BYTE  Data4[8];  

   } OLE\_GUID;


 


**Description :**



This is
taken directly from OLE's compobj.h.  The reason it's copied rather than
included here is to eliminate inclusion of the OLE2 header files, which without
great pain, only compile on OLE platforms.  This header file is included on ALL
Notes platforms, so we don't want to mess with the whole of OLE just for the
GUID typedef...


 




----------------------------------------------------------------------------------------------------------


 





