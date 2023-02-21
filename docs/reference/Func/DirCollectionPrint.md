##### Function : Dir
##### DirCollectionPrint - Prints a DIRCOLLECTION's contents using a supplied println() routine.
---
```
#include <dircoll.h>
void LNPUBLIC DirCollectionPrint(

	const DIRCOLLECTION  hCollection,
	int  printflags,
	DIRPRINTLN_PROC  println,
	void *ctx);
```
**Description :**

Prints a DIRCOLLECTION's contents using a supplied println() routine.

**Parameters :**
Input :
hCollection  -  Directory collection to print

printflags  -  OR-ed set of DIRPRINT_FLAG values

println  -  Print routine (e.g., DirPrintln())

ctx  -  println()-specific context



**See Also :**
[DirCollectionFirstEntry](/domino-c-api-docs/reference/Func/DirCollectionFirstEntry)
[DirCollectionFree](/domino-c-api-docs/reference/Func/DirCollectionFree)
[DirCollectionGetNumEntries](/domino-c-api-docs/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNextEntry](/domino-c-api-docs/reference/Func/DirCollectionNextEntry)
[DirCollectionNthEntry](/domino-c-api-docs/reference/Func/DirCollectionNthEntry)
---
