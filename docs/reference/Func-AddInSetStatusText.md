##### Function : AddIn
##### AddInSetStatusText - Set the status string of a Server Add-in task's default status line.
---
##### #include <addin.h>
void LNVARARGS **AddInSetStatusText(**

	char far *String,
	<Any 'C' type>  optional_var1, ...);
**Description :**
This function formats a string, and sets the status string of the current 
add-in task's default status line to the formatted string.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column).

Domino creates a default status line for add-in tasks that use AddInMain() as 
the entry point.  AddInSetStatusText() sets the status string of the current 
add-in task's default status line.

AddInSetStatusText() formats a status string based on the parameters. The 
String may contain up to four printf-type format specifiers.  If it does 
contain printf-type format specifiers, the remaining parameters must be 
printf-type arguments that resolve each of the format specifiers.  Up to 12 
bytes of additional parameters may be specified.  This function performs a 
function similar to "printf".  Pointer values passed for these arguments, such 
as the addresses of strings, must be "far" pointers.  The print format 
specifiers supported by Domino are described in the Tech Note "Domino Print 
Format Specifiers".  Tech Notes are listed in the view, Reference Tools/Tech 
Notes.

This function has no effect unless called from a Lotus Domino Server add-in 
task.
**Parameters :**
Input :
String  -  String that describes the Addin's current "state".  The string may contain up to four printf-type (%) format specifiers.  For each format specifier, a corresponding argument must be specified to resolve the format specifier.

optional_var1, ...  -  From 0 to 12 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the String argument.  All pointer values must be "far".  Leave off this parameter entirely (use only the above argument) if there are no format specifiers in the format string.

Output :
(routine)  -  None


**Sample Usage :**
```
if (AddInDayHasElapsed())
{
    AddInSetStatusText("Doing daily job");
    AddInLogMessageText("Addin Test: Daily job complete.", 
                        NOERROR);
    AddInSetStatusText("Idle");
}
```
**See Also :**
[AddInSetStatus](D:/md_files/AddInSetStatus.md)
[AddInMain](D:/md_files/AddInMain.md)
[AddInFormatError](D:/md_files/AddInFormatError.md)
[AddInLogError](D:/md_files/AddInLogError.md)
[AddInLogMsg](D:/md_files/AddInLogMsg.md)
---
