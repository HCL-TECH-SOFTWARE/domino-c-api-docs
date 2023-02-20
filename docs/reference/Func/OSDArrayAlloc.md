##### Function : Dynamic Array
##### OSDArrayAlloc - Create a dynamic array.
---
```
#include <darray.h>
STATUS LNPUBLIC OSDArrayAlloc(

	WORD  ElementSize,
	WORD  StringsPerElement,
	WORD  InitialElements,
	WORD  InitialStringStorage,
	DHANDLE far *rethDArray,
	DARRAY far * far *retDArray);
```
**Description :**

A Domino memory object is allocated and initialized to store a dynamic array.  
The entire DARRAY must fit within one memory segment;  the maximum size 
supported is MAXONESEGSIZE.

The elements stored in a dynamic array must have a basic structure that is 
fixed in size.  Elements may optionally have string components that are 
variable in size.  For each variable component, the fixed structure must 
contain a member of type PSTRING.  The PSTRING members must be the last members 
of the element structure.

The amount of memory allocated when the dynamic array is initialized is 
sizeof(DARRAY) + (ElementSize * InitialElements) + InitialStringStorage.  As 
elements are added, the dynamic array will increase in size;  as elements are 
removed, the dynamic array will shrink.  If the operating system supports 
reducing the size of a memory object, the memory actually required for the 
dynamic array will also shrink.

OSDArrayAlloc() sets default values for the number of extra elements (2) and 
the amount of extra packed string storage (64 bytes) to allocate when 
increasing the size of the dynamic array, and the maximum number of free 
elements (3) and the maximum amount of packed string storage (128 bytes) to 
allow before freeing memory.  These default values may be modified by using 
OSDArraySetFreeSizes().

The application must ensure that the memory object containing the dynamic array 
is freed by passing the handle to OSMemFree(), or by passing the dynamic array 
to a C API function that expects to free the storage.

**Parameters :**
Input :
ElementSize  -  Size of the structure stored for each element.

StringsPerElement  -  Number of PSTRING structures contained in each element.  The PSTRING members must be the last members of the structure.

InitialElements  -  Number of elements to allocate initially.

InitialStringStorage  -  Number of bytes to allocate initially for storing packed strings.

Output :
(routine)  -  Error status code for allocate operation.  NOERROR if successful, or if not, one of the following:

ERR_MEMORY - Not enough global memory available for allocation.
ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported.


rethDArray  -  The handle to the memory object containing the dynamic array is stored at this address.

retDArray  -  The pointer to the DARRAY structure is stored at this address.


**Sample Usage :**
```
		/* Structure for dynamic array elements */
typedef struct {
 WORD  num;
 PSTRING key;  /* Note that the PSTRING structures */
 PSTRING val;  /* are at the end!!   */
} KEY_LIST_ENTRY;
#define KEY_LIST_ENTRY_STRINGS 2 /* Number of PSTRINGs */

STATUS  status; /* Domino or Notes return code */
DHANDLE  hArray;
DARRAY far * pArray;
	
 /* Create dynamic array */
status = OSDArrayAlloc (
 sizeof (KEY_LIST_ENTRY), /* ElementSize  */
 KEY_LIST_ENTRY_STRINGS,  /* StringsPerElement */
 4,     /* InitialElements - start with 4! */
 128,     /* InitialStringStorage */
 &hArray,    /* Put handle here */
 &pArray);    /* Put pointer here */

```
**See Also :**
[DARRAY](/reference/Data/DARRAY)
[OSDArrayAddElement](/reference/Func/OSDArrayAddElement)
[OSDArrayRemoveElement](/reference/Func/OSDArrayRemoveElement)
[OSMemFree](/reference/Func/OSMemFree)
[PSTRING](/reference/Data/PSTRING)
[OSDArraySetFreeSizes](/reference/Func/OSDArraySetFreeSizes)
---
