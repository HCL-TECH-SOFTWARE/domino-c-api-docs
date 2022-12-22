




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




 


**Symbolic Value : OS Memory**



**MEM\_xxx** **-** Type of
memory block to be allocated in OSMemAlloc.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**


 **Symbolic Values :**      MEM\_SHARE           -  Allocated memory is to be shared
between processes.  

  

      MEM\_GROWABLE   -  This flag must be set when first allocating a
resizeable buffer (a buffer whose size can be reallocated to a different size
later). Despite its name, this flag must be set whether reallocation is used to
increase OR decrease the buffer's size.  

  




**Description :**



These flags
are used by OSMemAlloc and OSMemoryAllocate to specify the type of block to be
allocated.  0 may be specified if none of these types is applicable.


 **See Also :**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemRealloc](OSMemRealloc.md)**



----------------------------------------------------------------------------------------------------------


 





