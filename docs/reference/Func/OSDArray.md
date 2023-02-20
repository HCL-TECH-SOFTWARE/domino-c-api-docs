##### Function : Dynamic Array
##### OSDArray - Return a pointer to the elements in the dynamic array.
---
```
#include <darray.h>
<elementtype> far * OSDArray(

	DARRAY far *darray,
	<any>  elementtype);
```
**Description :**

A Domino dynamic array has three components - a header structure (DARRAY), an 
array of element structures, and storage for packed strings.  This function 
returns a pointer to the start of the array of element structures.

This function is currently implemented as a macro.

**Parameters :**
Input :
darray  -  Pointer to the dynamic array.

elementtype  -  Structure name of elements in the dynamic array.

Output :
(routine)  -  Pointer to the array of elements.  The type of the pointer depends on the elementtype argument.



**Sample Usage :**
```
	/* Structure for dynamic array elements */
typedef struct {
 WORD  num;
 PSTRING key;  /* Note that the PSTRING structures */
 PSTRING val;  /* are at the end!!   */
} KEY_LIST_ENTRY;
#define KEY_LIST_ENTRY_STRINGS 2 /* Number of PSTRINGs */

KEY_LIST_ENTRY far *pEntry; /* Pointer to current entry */
char far *  pKey;  /* Pointer to key string */
char far *  pVal;  /* Pointer to value string */
int   index;

	/* Get the address of an entry */
pEntry = &(OSDArray (pArray, KEY_LIST_ENTRY)[entryNumber]);

	/* Get addresses of packed strings */
	/* These strings do NOT have terminating NUL characters! */
pKey = OSDArrayString (pArray, pEntry->key);
pVal = OSDArrayString (pArray, pEntry->val);

	/* Print the contents of the entry */
printf ("Entry #%d:\tNumber: %d\tKey: ", index, pEntry->num);
for (index = 0; index < pEntry->key.StringSize; index++)
 putchar (pKey[index]);
printf ("\tValue: ");
for (index = 0; index < pEntry->val.StringSize; index++)
 putchar (pVal[index]);
putchar ('\n');

```
**See Also :**
[DARRAY](/reference/Data/DARRAY)
[PSTRING](/reference/Data/PSTRING)
---
