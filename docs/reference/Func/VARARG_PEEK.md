##### Function : Extension Manager
##### VARARG_PEEK - Peek at an argument from a variable argument list (no advance).
---
```
#include <global.h>
<type> VARARG_PEEK(

	VARARG_PTR  ap,
	<type>  Type);
```
**Description :**

Retrieve a value from a variable argument list, but do not advance the argument 
list pointer.  This function is implemented as a macro.

A pointer into a variable argument list is declared using the macro VARARG_PTR 
and initialized using the VARARG_START() macro.  Retrieving data from the 
variable argument list with VARARG_GET() will update the argument list pointer 
to point to the next argument, while retrieving the value using VARARG_PEEK() 
will obtain the value without updating the argument list pointer.  The argument 
type information is used to determine how large the argument value is, and is 
used in a typecast to ensure that assignment of the value is correct.

**Parameters :**
Input :
ap  -  Current pointer into the variable argument list.

Type  -  This must be a valid elementary data type.  Some examples of elementary data types are "int", "WORD", "char", "DWORD", "char *", or "BOOL".

Output :
(routine)  -  The type of the return value is specified by the "Type" argument.



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
[EMHANDLER](/domino-c-api-docs/reference/Data/EMHANDLER)
[EMRECORD](/domino-c-api-docs/reference/Data/EMRECORD)
[VARARG_GET](/domino-c-api-docs/reference/Func/VARARG_GET)
[VARARG_PTR](/domino-c-api-docs/reference/Data/VARARG_PTR)
[VARARG_START](/domino-c-api-docs/reference/Func/VARARG_START)
---
