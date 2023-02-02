##### Function : Main Routines
##### NotesLibraryMain - * OBSOLETE * Provide the address of a library initialization routine to Notes.  For NLM applications only.
---
##### #include <global.h>
STATUS LNPUBLIC **NotesLibraryMain(**

	int  argc,
	char far * far *argv,
	EXPORTED_LIBRARY_PROC  initproc);
**Description :**
This function allows you to create NLM custom executable program libraries that 
are called by Notes.  Note Open/Note Update Hook Drivers and external database 
drivers are examples of custom executable program libraries.

To create a custom executable program library under NetWare, create a main 
program.  In the main program, call this function to provide the address of the 
custom library's initialization routine.

The argc and argv arguments are the same as those passed to the application's 
main function.  The initproc argument is a function pointer to the custom 
library initialization routine.

**Parameters :**
Input :
argc  -  The number of command line arguments the program was invoked with

argv  -  Far pointer to an array of far pointers to null-terminated character strings that contain the arguments the program was invoked with


initproc  -  Function pointer to the custom library's initialization routine

Output :
(routine)  -  NOERROR if successfull, or a non-zero return value if not successful


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
[EXPORTED_LIBRARY_PROC](D:/md_files/EXPORTED_LIBRARY_PROC.md)
---
