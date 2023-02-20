##### Function : AddIn
##### AddInLogErrorText - Format and write error message to the log file.
---
```
#include <addin.h>
void LNPUBLIC AddInLogErrorText(

	char far *String,
	STATUS  AdditionalErrorCode,
	char far *Arg);
```
**Description :**

AddInLogErrorText formats an error message, displays it on the standard output, 
and appends the message as new line to the "Events" field in a Miscellaneous 
Events document in the Domino server or Notes client Log.  The generated 
message has the form:
 
          <DATE>  <TIME>  <Primary status message>: <Secondary status message>

The first parameter, String, is the primary status message. The second 
parameter, AdditionalErrorCode, may be a string resource ID, or it may be the 
STATUS returned from a C API function.

The String parameter may contain a printf-type format specifier. If it does, 
the last parameter, Arg, must point to a printf-type argument that resolves the 
format specifier.  Only one format specifier argument is supported in this 
function.  Use AddInLogMessageText if more than one format specifier argument 
is needed.  The print format specifiers supported by Domino are described in 
the Tech Note "Domino Print Format Specifiers".  Tech Notes are listed in the 
view, Reference Tools/Tech Notes.

AddInLogErrorText formats the Primary status message using String and, 
optionally, Arg.  It formats the Secondary status message using the Domino 
error message associated with the second parameter, AdditionalErrorCode.

AddInLogErrorText may be called from a NotesMain, main, or AddInMain API 
program. 

When using this function, you should call either AddInIdle or AddInIdleDelay on 
a regular basis to flush the log entries from memory to disk and free up the 
memory.

**Parameters :**
Input :
String  -  Primary status message which may contain up to one printf-type (%) format specifier which will get formatted using the 3rd argument.

AdditionalErrorCode  -  Secondary status code or message string resource ID.  If not used, specify NOERROR.

Arg  -  Pointer to an argument to be formatted into the  printf-type (%) format specifier in the string specified by StringID. Specify NULL if primary message string contains no format specifier.

Output :
(routine)  -  None



**See Also :**
[AddInFormatErrorText](/reference/Func/AddInFormatErrorText)
[AddInSetStatusText](/reference/Func/AddInSetStatusText)
[AddInLogMessageText](/reference/Func/AddInLogMessageText)
[LogEventText](/reference/Func/LogEventText)
[AddInLogError](/reference/Func/AddInLogError)
---
