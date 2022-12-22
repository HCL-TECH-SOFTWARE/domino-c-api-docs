




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



**OSDArrayRemoveElement** **- Remove an
element of a dynamic array.**


**----------------------------------------------------------------------------------------------------------**



**#include <darray.h>**



STATUS
LNPUBLIC **OSDArrayRemoveElement(**  

      DHANDLE  hDArray,  

      DARRAY far \* far \*DArray,  

      WORD  Index**);**



**Description :**



Remove the
specified element from the dynamic array.  Elements following the specified
element are moved to "fill in the hole" left by removing the
element.  If the operating system supports reducing the size of a memory
object, memory space may be freed by this operation.


 


**Parameters :**



Input :  

hDArray  -  Handle to the dynamic array.  

  

DArray  -  Address of the pointer to the dynamic array.  

  

Index  -  Index of the element to be removed.  

  




Output :  

(routine)  -  Error status code for operation, or NOERROR if successful.  

  

  

DArray  -  The address of the dynamic array may be changed by this operation; 
the address is stored at this address.  

  




 **Sample Usage :**



STATUS  status;


WORD           index;


 


        /\*
Remove the middle element of the array \*/  

index = pArray->ElementsUsed / 2;  

status = OSDArrayRemoveElement (hArray, &pArray, index);


 **See Also :**


**[DARRAY](DARRAY.md)**


**[OSDArrayAddElement](OSDArrayAddElement.md)**


**[OSDArrayAlloc](OSDArrayAlloc.md)**



----------------------------------------------------------------------------------------------------------


 





