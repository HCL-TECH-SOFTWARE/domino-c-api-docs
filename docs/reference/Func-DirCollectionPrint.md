##### Function : Dir
##### DirCollectionPrint - Prints a DIRCOLLECTION's contents using a supplied println() routine.
---
##### #include <dircoll.h>
void LNPUBLIC **DirCollectionPrint(**

	const DIRCOLLECTION  hCollection,
	int  printflags,
	DIRPRINTLN_PROC  println,
	void *ctx);
**Description :**
Prints a DIRCOLLECTION's contents using a supplied println() routine.
**Parameters :**
Input :
hCollection  -  Directory collection to print

printflags  -  OR-ed set of DIRPRINT_FLAG values

println  -  Print routine (e.g., DirPrintln())

ctx  -  println()-specific context


**See Also :**
[DirCollectionFirstEntry](D:/md_files/DirCollectionFirstEntry.md)
[DirCollectionFree](D:/md_files/DirCollectionFree.md)
[DirCollectionGetNumEntries](D:/md_files/DirCollectionGetNumEntries.md)
[DirCollectionNextEntry](D:/md_files/DirCollectionNextEntry.md)
[DirCollectionNthEntry](D:/md_files/DirCollectionNthEntry.md)
---
