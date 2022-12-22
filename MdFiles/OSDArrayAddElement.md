




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



**OSDArrayAddElement** **- Add an
element to a dynamic array.**


**----------------------------------------------------------------------------------------------------------**



**#include <darray.h>**



STATUS
LNPUBLIC **OSDArrayAddElement(**  

      DHANDLE  hDArray,  

      DARRAY far \* far \*DArray,  

      void far \*NewElement,  

      WORD  NewIndex**);**



**Description :**



Insert a new
element in a dynamic array.  All fields in the element structure should be set
before adding the element to the dynamic array.  In particular, the size and
address of the PSTRING elements must all be set.


 


The location
for the new element is specified by the NewIndex argument.  If NewIndex is
greater than the current number of element in the dynamic array, the new
element is appended to the end.  If NewIndex is less than the current number of
elements, the existing elements are move to accomodate the new element and the
new element is inserted at that index.


 


**Parameters :**



Input :  

hDArray  -  Handle to the dynamic array memory object.  

  

DArray  -  Address of the pointer to the dynamic array.  

  

NewElement  -  Pointer to the element to add to the dynamic array.  Any PSTRING
members must be initialized with the size and pointer to the string data.  

  

NewIndex  -  Index into the dynamic array where the element is to be inserted.  

  




Output :  

(routine)  -  Error status code for operation.  NOERROR if successful, or if
not, one of the following:  

  

ERR\_MEMORY - Not enough global memory available for allocation.  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported.  

  

  

DArray  -  The pointer to the dynamic array may be modified by this function; 
the pointer is stored at this address.  

  




 **Sample Usage :**


        /\* Structure
for dynamic array elements \*/


typedef
struct {  

        WORD           num;  

        PSTRING key;           /\* Note that the PSTRING structures   \*/  

        PSTRING val;           /\* are at the end!!                   \*/  

} KEY\_LIST\_ENTRY;  

#define KEY\_LIST\_ENTRY\_STRINGS 2      /\* Number of PSTRINGs \*/


 


STATUS         status; /\*
Notes return code \*/


DHANDLE        hArray;  

DARRAY far \*   pArray;


KEY\_LIST\_ENTRY
        entry;  /\* New entry \*/


WORD                   index
= 3;     /\* Insert as 3rd element \*/


WORD                   newNum
= 7;    /\* Data for new entry \*/


char far \*             pKey
= "Here's the key";


char far \*             pVal
= "The value!";  

          

        /\* Create dynamic array \*/  

status = OSDArrayAlloc (  

        sizeof (KEY\_LIST\_ENTRY),      /\* ElementSize         \*/  

        KEY\_LIST\_ENTRY\_STRINGS,               /\* StringsPerElement   \*/  

        4,                                    /\* InitialElements - start with
4! \*/  

        128,                                  /\* InitialStringStorage       \*/  

        &hArray,                              /\* Put handle here \*/  

        &pArray);                             /\* Put pointer here \*/


if (NOERROR
!= status)


        return
(status);


 


        /\*
Build the element record \*/


entry.num =
newNum;  

entry.key.StringSize = strlen (pKey);  

entry.key.StringType = 0;  

entry.key.String = pKey;  

entry.val.StringSize = strlen (pVal);  

entry.val.StringType = 0;  

entry.val.String = pVal;


 


        /\*
Add the element to the array \*/


status =
OSDArrayAddElement (hArray, &pArray, &entry, index);


 


 **See Also :**


**[DARRAY](DARRAY.md)**


**[OSDArrayAlloc](OSDArrayAlloc.md)**


**[OSDArrayRemoveElement](OSDArrayRemoveElement.md)**


**[PSTRING](PSTRING.md)**



----------------------------------------------------------------------------------------------------------


 





