




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Function : Dynamic Array**



**OSDArraySetFreeSizes** **- Modify
allocation rules for dynamic array.**


**----------------------------------------------------------------------------------------------------------**



**#include <darray.h>**



STATUS
LNPUBLIC **OSDArraySetFreeSizes(**  

      DARRAY far \*DArray,  

      WORD  ElementsFreeExtra,  

      WORD  ElementsFreeMax,  

      WORD  StringStorageFreeExtra,  

      WORD  StringStorageFreeMax**);**



**Description :**



When a
dynamic array is created, default values are set for the following control
parameters:


 


Number of
spare elements to allocate when memory space is increased:  2


Maximum
number of elements to retain before freeing extra memory:  3


Amount of
packed string storage to allocate when memory space is increased:  64 bytes


Maximum
amount of packed string storage to retain before freeing extra memory:  128
bytes


 


These
parameters can be modified with OSDArraySetFreeSizes().


 


**Parameters :**



Input :  

DArray  -  Handle of the dynamic array memory object.  

  

ElementsFreeExtra  -  New number of extra free elements to allocate.  

  

ElementsFreeMax  -  New maximum number of free elements to retain.  

  

StringStorageFreeExtra  -  New amount of extra string storage to allocate.  

  

StringStorageFreeMax  -  New maximum amount of string storage to retain.  

  




Output :  

(routine)  -  Error status code for operation, or NOERROR if successful.  

  

  




 **Sample Usage :**



STATUS  status;


 


status =
OSDArraySetFreeSizes (


    pArray,            /\*
Pointer to the dynamic array \*/


    12,        /\*
Allocate space for 12 more \*/


    24,        /\*
Release more than 24 free spaces \*/


    256,               /\*
Additional string space \*/


    1024);             /\*
Allow up to 1k of spare space \*/


 **See Also :**


**[DARRAY](DARRAY.md)**


**[OSDArrayAlloc](OSDArrayAlloc.md)**



----------------------------------------------------------------------------------------------------------


 





