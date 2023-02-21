##### Function : Dynamic Array
##### OSDArrayString - Return pointer to packed string.
---
```
#include <darray.h>
char far * OSDArrayString(

	DARRAY far *darray,
	PSTRING  pstring);
```
**Description :**

Return a pointer to the packed string for an element of a dynamic array.

This function is currently implemented as a macro.

**Parameters :**
Input :
darray  -  Pointer to the dynamic array.

pstring  -  Packed string structure in the desired element structure.

Output :
(routine)  -  Pointer to the packed string.



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
[OSDArray](/domino-c-api-docs/reference/Func/OSDArray)
[PSTRING](/domino-c-api-docs/reference/Data/PSTRING)
[DARRAY](/domino-c-api-docs/reference/Data/DARRAY)
---
