




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




 


**Data Type : Dynamic Array**



**DARRAY** **-** Dynamic
array header structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<darray.h>**



**Definition :**



typedef struct {  

    WORD ObjectSize;             /\* Total array object size \*/  

    WORD ElementsUsed;           /\* Elements in use \*/  

    WORD ElementsFree;           /\* Free elements \*/  

    WORD ElementsFreeMax;        /\* Maximum free elements \*/  

    WORD ElementsFreeExtra;      /\* Extra free elements to maintain \*/  

    WORD ElementSize;            /\* Element size in bytes \*/  

    WORD ElementStrings;         /\* Number packed string descriptors  

                                    in each element \*/  

    WORD StringStorageOffset;    /\* Offset to packed string storage \*/  

    WORD StringStorageUsed;      /\* In use bytes of string storage \*/  

    WORD StringStorageFree;      /\* Free bytes of string storage \*/  

    WORD StringStorageFreeMax;   /\* Maximum free storage \*/  

    WORD StringStorageFreeExtra; /\* Extra free storage to maintain \*/  

  

/\*  First array element follows here.  First byte of packed string  

/\*  storage follows last allocated array element. \*/  

  

} DARRAY;


 


**Description :**



Dynamic
arrays are used internally by Domino and Notes to manage collections of
information in memory that require frequent insertions and deletions.  A
dynamic array has three components:


 


1)  The
DARRAY structure, which contains control information.


2)  An array
of element structures of fixed size.


3)  Storage
for packed strings;  strings can have any length, and are described by PSTRING
structures contained in the element structures.


 


The element
structures can be any size, but all element structures in one DARRAY must be
the same size.  Any PSTRING structures must be the last members of the element
structures.


 


The size of
the entire dynamic array cannot exceed MAXONESEGSIZE in size.


 **See Also :**


**[MAXONESEGSIZE](MAXONESEGSIZE.md)**


**[PSTRING](PSTRING.md)**


**[OSDArray](OSDArray.md)**


**[OSDArrayAddElement](OSDArrayAddElement.md)**


**[OSDArrayAlloc](OSDArrayAlloc.md)**


**[OSDArrayRemoveElement](OSDArrayRemoveElement.md)**



----------------------------------------------------------------------------------------------------------


 





