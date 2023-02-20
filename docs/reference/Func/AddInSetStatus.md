##### Function : AddIn
##### AddInSetStatus - Set the status string of a Server Add-in task's default status line. Uses string resources.
---
```
#include <addin.h>
void LNVARARGS AddInSetStatus(

	STATUS  StringID,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

This function formats a string and sets the status string of the current add-in 
task's default status line to the formatted string.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column).

Domino creates a default status line for add-in tasks that use AddInMain() as 
the entry point.  AddInSetStatus() sets the status string of the current add-in 
task's default status line.

AddInSetStatus() formats a status string based on the parameters. The StringID 
parameter is a string resource ID that identifies a string in the string table 
attached to the calling program's executable file.  The string may contain up 
to four printf-type format specifiers.  If it does contain printf-type format 
specifiers, the remaining parameters must be printf-type arguments that resolve 
each of the format specifiers.  Up to 12 bytes of additional parameters may be 
specified.  This function performs a function similar to "printf", except that 
it works with Domino string resources.  Pointer arguments, such as pointers to 
"C" strings, must be "far" pointers.  The print format specifiers supported by 
Domino are described in the Tech Note "Domino Print Format Specifiers".  Tech 
Notes are listed in the view, Reference Tools/Tech Notes.

This function has no effect unless called from a Lotus Domino Server add-in 
task. 

This function only supports message strings that are stored as string resources 
and therefore is not portable across all types of platforms.  Use the function, 
AddInSetStatusText() for platforms that do not support string resources.

**Parameters :**
Input :
StringID  -  Resource ID of string describing Addin's current "state".  The string may contain up to four printf-type (%) format specifiers.  For each format specifier, a corresponding argument must be specified to resolve the format specifier.

optional_var1, ...  -  From 0 to 12 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the format string associated with the StringID argument.  All pointer values must be "far".  Leave off this parameter entirely (use only the above argument) if there are no format specifiers in the format string.

Output :
(routine)  -  None



**Sample Usage :**
```

/* Constants & corresponding Strings built into AddIn's string table.*/
/* #define MSG_SMKADDN_RUNNING                    (PKG_ADDIN+9)      */
/*        msgtext(MSG_SMKADDN_RUNNING,           "Running")          */

   /* Set task status to "Running" for server console */

   AddInSetStatus(MSG_SMKADDN_RUNNING);

```
**See Also :**
[AddInSetStatusText](/reference/Func/AddInSetStatusText)
[AddInMain](/reference/Func/AddInMain)
[AddInFormatError](/reference/Func/AddInFormatError)
[AddInLogError](/reference/Func/AddInLogError)
[AddInLogMsg](/reference/Func/AddInLogMsg)
---
