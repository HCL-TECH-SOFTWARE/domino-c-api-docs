##### Function : OS Program
##### OSLoadProgram - Load and execute an external Program.
---
##### #include <osmisc.h>
STATUS LNPUBLIC **OSLoadProgram(**

	char far *filename,
	char far *WorkingDir,
	char far *Arguments,
	WORD  Flags);
**Description :**
This function loads and executes an external Program. Use OSLoadProgram to load 
and execute software modules at run time. 

OSLoadProgram provides C API programs with a platform-independent procedure for 
loading and executing a program.

Starting with Release 4.6, the command line is assumed to be in LMBCS, the 
Lotus Multi-Byte Character Set, and is translated to the operating system's 
native character set before being passed to the called program.

**Parameters :**
Input :
filename  -  File name of the executable program to load and execute.

WorkingDir  -  If "WorkingDir" is not NULL, the specified directory is made to be the current directory before program execution, else it is the directory that the program lives in.

Arguments  -  Optional command line arguments to be used when launching the program.  The command line arguments are translated from LMBCS to the native character set.

Flags  -  Define how to execute the program. Use one of the OS_LOADPROG_xxx flags symbolic values.

Output :
(routine)  -  Completion status of the operation, NOERROR if successful.


**Sample Usage :**
```
STATUS error;
char ProgramPath[MAXPATH];
WORD Flags = OS_LOADPROG_BACKGROUND | OS_LOADPROG_ICONIC |
     OS_LOADPROG_DEBUG;

/* Set your program  pathname  ProgramPath */
            < ..............>

/* Load the program  with "-w" command line argument: */

 error = OSLoadProgram(ProgramPath, NULL, "-w", Flags);

```
**See Also :**
[OS_LOADPROG_xxx](D:/md_files/OS_LOADPROG_xxx.md)
---
