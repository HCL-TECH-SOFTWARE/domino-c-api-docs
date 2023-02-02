##### Function : Dynamic Array
##### OSDArraySetFreeSizes - Modify allocation rules for dynamic array.
---
##### #include <darray.h>
STATUS LNPUBLIC **OSDArraySetFreeSizes(**

	DARRAY far *DArray,
	WORD  ElementsFreeExtra,
	WORD  ElementsFreeMax,
	WORD  StringStorageFreeExtra,
	WORD  StringStorageFreeMax);
**Description :**
When a dynamic array is created, default values are set for the following 
control parameters:

Number of spare elements to allocate when memory space is increased:  2
Maximum number of elements to retain before freeing extra memory:  3
Amount of packed string storage to allocate when memory space is increased:  64 
bytes
Maximum amount of packed string storage to retain before freeing extra memory:  
128 bytes

These parameters can be modified with OSDArraySetFreeSizes().
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
```
STATUS status;

status = OSDArraySetFreeSizes (
	pArray,  /* Pointer to the dynamic array */
	12,  /* Allocate space for 12 more */
	24,  /* Release more than 24 free spaces */
	256,  /* Additional string space */
	1024);  /* Allow up to 1k of spare space */
```
**See Also :**
[DARRAY](D:/md_files/DARRAY.md)
[OSDArrayAlloc](D:/md_files/OSDArrayAlloc.md)
---
