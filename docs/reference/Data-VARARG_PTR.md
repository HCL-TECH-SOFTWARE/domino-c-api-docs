##### Data Type : Extension Manager
##### VARARG_PTR - Pointer to a variable argument list.
---
##### #include <global.h>
**Description :**
The VARARG macros support access to variable argument lists.  These argument 
lists appear in the C API in two places, functions with "cdecl" argument lists 
and in the Extension Manager facility.

VARARG_PTR is a type definition for a pointer into a variable argument list.  
This pointer is initialized by the VARARG_START() macro.  The pointer is then 
used in the VARARG_GET(), and VARARG_PEEK() macros to access elements of the 
argument list.
**Sample Usage :**
```
void far cdecl SampleRoutine (
	char *String,
	WORD LastNamedArgument, ...)
{
  DWORD temp1;
  WORD  temp2;
  VARARG_PTR ap;

  VARARG_START(ap,LastNamedArgument);
        /* Start out just past last named argument */
  temp1 = VARARG_GET(ap,DWORD);
        /* Get next DWORD into temp1 and advance */
  temp2 = VARARG_PEEK(ap,WORD);
        /* Peek at next WORD, but no advance */
  temp2 = VARARG_GET(ap,WORD);
        /* Get next WORD into temp2 and advance */
}
```
**See Also :**
[VARARG_GET](D:/md_files/VARARG_GET.md)
[VARARG_PEEK](D:/md_files/VARARG_PEEK.md)
[VARARG_START](D:/md_files/VARARG_START.md)
---
