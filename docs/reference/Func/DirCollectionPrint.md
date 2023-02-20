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
[DirCollectionFirstEntry](/reference/Func/DirCollectionFirstEntry)
[DirCollectionFree](/reference/Func/DirCollectionFree)
[DirCollectionGetNumEntries](/reference/Func/DirCollectionGetNumEntries)
[DirCollectionNextEntry](/reference/Func/DirCollectionNextEntry)
[DirCollectionNthEntry](/reference/Func/DirCollectionNthEntry)
---
