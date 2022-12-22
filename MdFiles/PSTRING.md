




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



**PSTRING** **-** Packed
string descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<darray.h>**



**Definition :**



typedef struct {  

    WORD StringSize;  /\* String size \*/  

    WORD StringType;  /\* String type (info only) \*/  

    char far \*String; /\* String pointer or offset \*/  

} PSTRING;


 


**Description :**



Structure
defining a packed string for a dynamic array.  This structure is incorporated
into a structure to be stored as an element in a dynamic array.  Any PSTRING
structures must be the last members of the element structure.


 


The member
StringType is optional, and may be used by applications to store any 16-bit
value.  The members StringSize and String are required, and must be set
correctly before the element is stored in the dynamic array.


 


Before an
element is stored in a dynamic array, the String member must be a pointer to
the packed string data.  This data need not be contiguous with the element
record.  Once the element is stored in the dynamic array, the String member in
the element record stored in the dynamic array becomes an offset into the
packed string store for that dynamic array.  (The original member structure is
not modified.)


 **See Also :**


**[DARRAY](DARRAY.md)**


**[OSDArrayAddElement](OSDArrayAddElement.md)**


**[OSDArray](OSDArray.md)**


**[OSDArrayRemoveElement](OSDArrayRemoveElement.md)**



----------------------------------------------------------------------------------------------------------


 





