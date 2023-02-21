##### Function : OS Environment Variables
##### OSSetEnvironmentVariable - Set an environment variable string.
---
```
#include <osenv.h>
void LNPUBLIC OSSetEnvironmentVariable(

	const char far *VariableName,
	const char far *Value);
```
**Description :**

OSSetEnvironmentVariable is used to set a Domino or Notes environment variable 
to the value of the specified string.   The specified environment variable can 
be existing or new.

Domino or Notes environment variables are stored in the file notes.ini.

**Parameters :**
Input :
VariableName  -  Pointer to the name of the environment variable.

Value  -  Pointer to a text buffer containing the new value of the environment variable as an null-terminated string.

Output :
(routine)  -  None.



**See Also :**
[OSGetEnvironmentString](/domino-c-api-docs/reference/Func/OSGetEnvironmentString)
[OSGetEnvironmentLong](/domino-c-api-docs/reference/Func/OSGetEnvironmentLong)
[OSGetEnvironmentInt](/domino-c-api-docs/reference/Func/OSGetEnvironmentInt)
[OSSetEnvironmentInt](/domino-c-api-docs/reference/Func/OSSetEnvironmentInt)
---
