##### Function : Extension Manager
##### VARARG_GET - Retrieve an argument from a variable argument list.
---
```
#include <global.h>
<type> VARARG_GET(

	VARARG_PTR  ap,
	<type>  Type);
```
**Description :**

This function is used to access the elements of a variable argument list to a 
function or to access the arguments of an API function in a Extension Manager 
callback.  This function is implemented as a macro.

A pointer into a variable argument list is declared using the macro VARARG_PTR 
and initialized using the VARARG_START() macro.  This pointer is used in the 
VARARG_GET() macro to obtain an argument value, and the VARARG_PTR is updated 
to point to the next argument value.  The argument type information is used to 
determine how large the argument value is, and is used in a typecast to ensure 
that assignment of the value is correct.

This macro can be used, for example, to retrieve the arguments passed to the 
callback procedure in the Extension Manager.  The Ap field in the EMRECORD 
structure contains a VARARG_PTR to the parameters passed to the core function.  
By using multiple calls to VARARG_GET each of the function arguments can be 
retrieved.

**Parameters :**
Input :
ap  -  Current pointer into the variable argument list.

Type  -  This must be a valid elementary data type.  Some examples of elementary data types are "int", "WORD", "char", "DWORD", "char *", or "BOOL".

Output :
(routine)  -  The type of the return value is specified by the "Type" argument.


ap  -  The variable argument list pointer is updated to point to the next argument.


**Sample Usage :**
```
/* Retrieving the parameters to NSFDBOPENEXTENDED. */

/* Declaration of the function we're examining:
    STATUS LNPUBLIC NSFDbOpenExtended (
	 char far *PathName,
  WORD Options,
  HANDLE hNames,
  TIMEDATE far *ModifiedTime,
  DBHANDLE far *rethDB,
  TIMEDATE far *retDataModified,
  TIMEDATE far *retNonDataModified);

If you only want the dbHandle, you still must retrieve all of the other 
parameters first.
*/
  DBHANDLE dbHandle;
  VARARG_PTR argPtr;  /* Initialize pointer */

  VARARG_GET( argPtr, char FAR * ); /* Skip PathName */
  VARARG_GET( argPtr, WORD );  /* Skip Options */
  VARARG_GET( argPtr, HANDLE );   /* Skip hNames */
  VARARG_GET( argPtr, TIMEDATE FAR * );/* Skip ModifiedTime */ 
  dbHandle = *( DBHANDLE FAR * )VARARG_GET( argPtr, DBHANDLE FAR *);
  VARARG_GET( argPtr, TIMEDATE FAR * );
  VARARG_GET( argPtr, TIMEDATE FAR * );
```
**See Also :**
[EMHANDLER](/reference/Data/EMHANDLER)
[EMRECORD](/reference/Data/EMRECORD)
[VARARG_PEEK](/reference/Func/VARARG_PEEK)
[VARARG_PTR](/reference/Data/VARARG_PTR)
[VARARG_START](/reference/Func/VARARG_START)
---
