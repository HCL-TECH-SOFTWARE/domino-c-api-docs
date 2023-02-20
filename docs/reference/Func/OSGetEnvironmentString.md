##### Function : OS Environment Variables
##### OSGetEnvironmentString - Gets the string value of an environment variable.
---
```
#include <osenv.h>
BOOL LNPUBLIC OSGetEnvironmentString(

	const char far *VariableName,
	char far *retValueBuffer,
	WORD  BufferLength);
```
**Description :**

OSGetEnvironmentString is used to get the value of a Domino or Notes 
environment variable string.  It takes the name of the environment variable, 
the address of a text buffer (up to MAXENVVALUE bytes), and the length of that 
buffer minus one (1).  It returns the null-terminated string currently 
associated with the environment variable.

Domino and Notes environment variables are stored in the notes.ini file.  
Environment variables can be set from the Lotus Domino Server Console.

Example:

From Server Console:
SET CONFIG TEST_STRING=THIS_IS_IT


**Parameters :**
Input :
VariableName  -  Pointer to name of the environment variable (null-terminated, case-insensitive)

BufferLength  -  (Size of buffer) - 1 (leaving 1 byte for a guaranteed NULL terminator)

Output :
(routine)  -  TRUE if specified variable was found, FALSE if not.


retValueBuffer  -  The address of an existing text buffer in which the null-terminated string value of the specified environment variable is returned.  Caller must preallocate space for the buffer (up to MAXENVVALUE bytes).


**See Also :**
[OSGetEnvironmentLong](/reference/Func/OSGetEnvironmentLong)
[OSSetEnvironmentVariable](/reference/Func/OSSetEnvironmentVariable)
[OSSetEnvironmentInt](/reference/Func/OSSetEnvironmentInt)
---
