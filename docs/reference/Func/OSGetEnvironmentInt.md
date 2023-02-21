##### Function : OS Environment Variables
##### OSGetEnvironmentInt - Return integer value of an environment variable.
---
```
#include <osenv.h>
int LNPUBLIC OSGetEnvironmentInt(

	char far *VariableName);
```
**Description :**

OSGetEnvironmentInt is a wrapper around the API OSGetEnvironmentLong.  It takes 
the specified envrironment string, converts the text associated with it into 
type "int", and returns that value to the current context.   

Domino and Notes environment variables are stored in notes.ini, and can be set 
from the Lotus Domino Server via the SET CONFIG console command.

Example (from Server Console):
SET CONFIG TEST_INTEGER=100


Note: this function is implemented as a macro:


#define OSGetEnvironmentInt(s) ((int) OSGetEnvironmentLong(s))

**Parameters :**
Input :
VariableName  -  Pointer to name of the environment variable (null-terminated, case-insensitive). 

Output :
(routine)  -  Integer value of variable;  0 if variable is not found or is not numeric.



**See Also :**
[OSGetEnvironmentLong](/domino-c-api-docs/reference/Func/OSGetEnvironmentLong)
[OSGetEnvironmentString](/domino-c-api-docs/reference/Func/OSGetEnvironmentString)
[OSSetEnvironmentVariable](/domino-c-api-docs/reference/Func/OSSetEnvironmentVariable)
[OSSetEnvironmentInt](/domino-c-api-docs/reference/Func/OSSetEnvironmentInt)
---
