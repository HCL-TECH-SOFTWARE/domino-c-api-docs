##### Symbolic Value : OS Program
##### OS_LOADPROG_xxx - OSLoadProgram - Flags
---
```
#include <osmisc.h>
```

**Symbolic Values :**

	OS_LOADPROG_ICONIC	  -  Don't show application window

	OS_LOADPROG_BACKGROUND	  -  Don't bring to the foreground

	OS_LOADPROG_DEBUG	  -  Start with QNC

	OS_LOADPROG_DETACHED	  -  Don't wait around for this process to exit

	OS_LOADPROG_ASSOCIATE	  -  Look for a file type association

	OS_LOADPROG_PRIORITY_LOW	  -  Start process with a lower priority

	OS_LOADPROG_SHELL_SCRIPT_USE_EXECVP	  -  Flag to signal a shell script, so we can use execvp instead of execv. Currently in use only on AIX

	OS_LOADPROG_OPEN_WITH	  -  Flag to add the necessary things to do an open with command. Currently on use only on NT


**Description :**

These symbols define how to execute the program in a call to OSLoadProgram.


**See Also :**
[OSLoadProgram](/domino-c-api-docs/reference/Func/OSLoadProgram)
---
