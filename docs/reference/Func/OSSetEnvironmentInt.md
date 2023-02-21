##### Function : OS Environment Variables
##### OSSetEnvironmentInt - Set an "integer" environment variable.
---
```
#include <osenv.h>
void LNPUBLIC OSSetEnvironmentInt(

	const char far *VariableName,
	int  Value);
```
**Description :**

OSSetEnvironmentInt is used to set the value of a Domino or Notes environment 
variable to the specified integer.  The environment variable can be an existing 
or new one.

**Parameters :**
Input :
VariableName  -  Pointer to the name of the environment variable.

Value  -  New value of the environment variable.

Output :
(routine)  -  None.



**See Also :**
[OSGetEnvironmentInt](/domino-c-api-docs/reference/Func/OSGetEnvironmentInt)
[OSGetEnvironmentLong](/domino-c-api-docs/reference/Func/OSGetEnvironmentLong)
[OSGetEnvironmentString](/domino-c-api-docs/reference/Func/OSGetEnvironmentString)
[OSSetEnvironmentVariable](/domino-c-api-docs/reference/Func/OSSetEnvironmentVariable)
---
