##### Function : OS Library
##### OSFreeLibrary - Free a library module that was previously loaded
---
```
#include <osmisc.h>
void LNPUBLIC OSFreeLibrary(

	HMODULE  hModule);
```
**Description :**

This function frees a library module that was previously loaded using 
OSLoadLibray and frees any resources associated with that module.

OSFreeLibrary provides a platform-independent procedure for API functions to 
free library modules loaded at run time.  Under Windows, OSFreeLibrary results 
in a call to FreeLibrary (see the Windows SDK Reference).

**Parameters :**
Input :
hModule  -  Module handle of the loaded library.  Obtain this handle from a previous call to OSLoadLibrary.



**See Also :**
[OSLoadLibrary](/reference/Func/OSLoadLibrary)
[IXENTRYPROC](/reference/Data/IXENTRYPROC)
---
