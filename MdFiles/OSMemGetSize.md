




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




 


**Function : OS Memory**



**OSMemGetSize** **- Get the
size of a Domino memory object.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemGetSize(**  

      DHANDLE  Handle,  

      DWORD far \*retSize**);**



**Description :**



OsMemGetSize
is used to get the size of an object in bytes.  This function may return a size
larger than the object was originally allocated, in the event that the
operating system rounded up the size to the nearest allocation boundary.  

  

Calling this routine with a HANDLE that is invalid or out of range will result
in a Notes PANIC Halt.


 


**Parameters :**



Input :  

Handle  -  Handle for the object whose size is to be returned  

  




Output :  

(routine)  -  Completion status of the operation -- Always returns NOERROR. 
There is no need to check the return value.  

  

  

retSize  -  The address of a DWORD in which the object size in bytes will be
returned.  

  




 **See Also :**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemRealloc](OSMemRealloc.md)**


**[OSMemFree](OSMemFree.md)**



----------------------------------------------------------------------------------------------------------


 





