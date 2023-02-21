##### Function : Full Text Search
##### NSFDbFTSizeGet - Get the total size of the full text index.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbFTSizeGet(

	const char far *Filename,
	DWORD *FTSize);
```
**Description :**

When a database is full text indexed, an index folder is created in the DATA 
directory.  This function retrieves the size of this folder and its contents.  
If the database is not full text indexed, the size will be set to zero.

**Parameters :**
Input :
Filename  -  The name of the database.

Output :
(routine)  -  Return status from this call indicates either success or what the error is. 


FTSize  -  The address of a DWORD in which the total size of a database's full text index is returned.  If the database is not full text indexed, the size will be set to zero.


**Sample Usage :**
```
 
DWORD FTSize;
.
.
/* Get the size of the Database's full text index file. */

if (error = NSFDbFTSizeGet(path_name, &FTSize))
{
   print_api_error(error);
}
else
{
   printf("\n FT size is %d\n",FTSize);
}
```
**See Also :**
[FTIndex](/domino-c-api-docs/reference/Func/FTIndex)
[FTSearch](/domino-c-api-docs/reference/Func/FTSearch)
[FTSearchExt](/domino-c-api-docs/reference/Func/FTSearchExt)
---
