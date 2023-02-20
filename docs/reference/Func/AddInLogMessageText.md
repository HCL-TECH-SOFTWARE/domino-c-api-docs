##### Function : AddIn
##### AddInLogMessageText - Format and write a message to the log file.
---
```
#include <addin.h>
void LNVARARGS AddInLogMessageText(

	char far *String,
	STATUS  AdditionalErrorCode,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

 This function formats a message, displays it on the standard output, and 
appends the message as new line to the "Events" field in a Miscellaneous Events 
document in the Domino server or Notes client log.  The generated message has 
the form:
 
          <DATE>  <TIME> <Primary status message>: <Secondary status message>

The first parameter, String, is the primary status message.   The second 
parameter, AdditionalErrorCode, may be a string resource ID, or it may be the 
STATUS returned from a C API function.

The string parameter may contain up to six printf-type format specifiers. If it 
does contain printf-type format specifiers, the last remaining parameters must 
be printf-type arguments that resolve each of the format specifiers.  Up to 24 
bytes of additional parameters may be specified.  Pointer values, such as 
string arguments, must be passed as "far" pointers.  The print format 
specifiers supported by Domino are described in the Tech Note "Domino Print 
Format Specifiers".  Tech Notes are listed in the view, Reference Tools/Tech 
Notes.

AddInLogMessageText formats the Primary status message using String and the 
last remaining parameters as described above.  It formats the Secondary status 
message using the error message associated with the second parameter, 
AdditionalErrorCode.

When using this function, you should call either AddInIdle or AddInIdleDelay on 
a regular basis to flush the log entries from memory to disk and free up the 
memory.

**Parameters :**
Input :
String  -  Primary status message which may contain up to six printf-type (%) format specifiers.  For each format specifier, a corresponding argument must be specified after the AdditionalErrorCode argument to resolve the format specifier.

AdditionalErrorCode  -  Secondary status code or message string resource ID.  If not used, specify NOERROR.

optional_var1, ...  -   From 0 to 24 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the String argument.  All pointer values must be "far".  Leave off this parameter entirely (use only the above 2 arguments) if there are no format specifiers in the format string.

Output :
(routine)  -  None



**See Also :**
[AddInLogError](/reference/Func/AddInLogError)
[AddInLogMessage](/reference/Func/AddInLogMessage)
[AddInLogMsg](/reference/Func/AddInLogMsg)
[AddInSetStatus](/reference/Func/AddInSetStatus)
---
