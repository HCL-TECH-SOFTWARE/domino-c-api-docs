##### Function : OS Environment Variables
##### OSGetEnvironmentLong - Return "long" value of an environment variable.
---
```
#include <osenv.h>
long LNPUBLIC OSGetEnvironmentLong(

	const char far *VariableName);
```
**Description :**

This function takes the specified environment string, converts the text 
associated with it into type "long", and returns that value to the current 
context.   

Domino or Notes environment variables are stored in notes.ini, and can be set 
from the Lotus Domino Server via the SET CONFIG console command.

Example (from Server Console):
SET CONFIG TEST_LONG=74000

**Parameters :**
Input :
VariableName  -  Pointer to name of the environment variable (null-terminated, case-insensitive).

Output :
(routine)  -  Long integer value of variable;  0 if variable is not found or is not numeric.



**See Also :**
[OSGetEnvironmentInt](/domino-c-api-docs/reference/Func/OSGetEnvironmentInt)
[OSGetEnvironmentString](/domino-c-api-docs/reference/Func/OSGetEnvironmentString)
[OSSetEnvironmentVariable](/domino-c-api-docs/reference/Func/OSSetEnvironmentVariable)
[OSSetEnvironmentInt](/domino-c-api-docs/reference/Func/OSSetEnvironmentInt)
---
