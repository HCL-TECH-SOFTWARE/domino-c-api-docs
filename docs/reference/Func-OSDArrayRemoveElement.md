##### Function : Dynamic Array
##### OSDArrayRemoveElement - Remove an element of a dynamic array.
---
##### #include <darray.h>
STATUS LNPUBLIC **OSDArrayRemoveElement(**

	DHANDLE  hDArray,
	DARRAY far * far *DArray,
	WORD  Index);
**Description :**
Remove the specified element from the dynamic array.  Elements following the 
specified element are moved to "fill in the hole" left by removing the 
element.  If the operating system supports reducing the size of a memory 
object, memory space may be freed by this operation.
**Parameters :**
Input :
hDArray  -  Handle to the dynamic array.

DArray  -  Address of the pointer to the dynamic array.

Index  -  Index of the element to be removed.

Output :
(routine)  -  Error status code for operation, or NOERROR if successful.


DArray  -  The address of the dynamic array may be changed by this operation;  the address is stored at this address.

**Sample Usage :**
```
STATUS status;
WORD  index;

	/* Remove the middle element of the array */
index = pArray->ElementsUsed / 2;
status = OSDArrayRemoveElement (hArray, &pArray, index);
```
**See Also :**
[DARRAY](D:/md_files/DARRAY.md)
[OSDArrayAddElement](D:/md_files/OSDArrayAddElement.md)
[OSDArrayAlloc](D:/md_files/OSDArrayAlloc.md)
---
