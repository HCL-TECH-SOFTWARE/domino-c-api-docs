##### Function : Extension Manager
##### VARARG_START - Initialize a variable argument list pointer.
---
##### #include <global.h>
void **VARARG_START(**

	VARARG_PTR  ap,
	<type>  LastNamedArg);
**Description :**
Initialize the pointer to a variable argument list.  This function is 
implemented as a macro.

The macro uses the address and size of the last named argument to the function 
to determine the location of the first argument in the variable part of the 
argument list.
**Parameters :**
Input :

LastNamedArg  -  Name of the last named (or fixed) argument in the variable argument list.

Output :
ap  -  The variable argument pointer is set to the first element in the variable argument list.

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
[EMHANDLER](D:/md_files/EMHANDLER.md)
[EMRECORD](D:/md_files/EMRECORD.md)
[VARARG_GET](D:/md_files/VARARG_GET.md)
[VARARG_PEEK](D:/md_files/VARARG_PEEK.md)
[VARARG_PTR](D:/md_files/VARARG_PTR.md)
---
