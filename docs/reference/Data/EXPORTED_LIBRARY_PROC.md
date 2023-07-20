##### Data Type : Main Routines
##### EXPORTED_LIBRARY_PROC - Pointer to a custom library's initialization routine.  For NLM applications only.
---
```
#include <global.h>
```

**Definition :**
```
typedef void EXPORTED_LIBRARY_PROC(void);
```

**Description :**

This is the definition of a pointer to a function that is a custom library's initialization routine.  It is used when calling the function, NotesLibraryMain() in order to provide the address of a custom library's initialization routine to Notes. 


**Sample Usage :**
```
	#ifdef NLM
STATUS LNPUBLIC DBDInit(DBVEC *drv);           /* Prototype for the
                                                    driver's entry point */
int main (int argc, char *argv[])
{
   /* Call the Notes routine, NotesLibraryMain, passing in a pointer
      to the hook driver's entry point.  Notes will then call this
      hook driver when appropriate. */

    return ( (int) NotesLibraryMain (
                      argc, argv,
                      (EXPORTED_LIBRARY_PROC *) DBDInit) );
}
#endif
```

**See Also :**
[NotesLibraryMain](/domino-c-api-docs/reference/Func/NotesLibraryMain)
---
