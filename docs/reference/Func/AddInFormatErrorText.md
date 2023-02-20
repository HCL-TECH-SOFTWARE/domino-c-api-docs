##### Function : AddIn
##### AddInFormatErrorText - Format an error string.
---
```
#include <addin.h>
void LNVARARGS AddInFormatErrorText(

	char far *retString,
	char far *String,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

AddInFormatErrorText is used to generate a formatted error message.  The 
message can then be used by the program for purposes other than standard AddIn 
logging, for example, updating the status display (see AddInSetStatusText).  

It can also be used to format an error message that requires more than one 
argument for its format string.  In this case, the formatted error string can 
then be passed to AddInLogErrorText as the Arg parameter with a text string 
containing a "%s" format specifier passed in as the String parameter.  However, 
the function, AddInLogMessageText, provides an easier way to accomplish this.

The second parameter to AddInFormatErrorText is a string that may contain up to 
four printf-type format specifiers.  If it does contain printf-type format 
specifiers, the remaining parameters must be printf-type arguments that resolve 
each of the format specifiers.  Up to 16 bytes of additional parameters may be 
specified.  The print format specifiers supported by Domino are described in 
the Tech Note "Domino Print Format Specifiers".  Tech Notes are listed in the 
view, Reference Tools/Tech Notes.

This function performs a function similiar to "sprintf".

**Parameters :**
Input :

String  -  The error text string.  This string may contain up to four printf-type (%) format specifiers. For each format specifier provided, there should be an additional argument provided for formatting into the message string.

optional_var1, ...  -  From 0 to 16 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the string loaded by the first argument. All pointer values must be "far".  Leave off this parameter entirely (use only the first two arguments) if there are no format specifiers in the format string.

Output :
(routine)  -  None


retString  -  The formatted message string is placed in the specified character buffer.  It is the caller's responsibility to allocate this buffer (MAXSPRINTF bytes) prior to making the call.


**See Also :**
[AddInLogErrorText](/reference/Func/AddInLogErrorText)
[AddInSetStatusText](/reference/Func/AddInSetStatusText)
[AddInLogMessageText](/reference/Func/AddInLogMessageText)
[AddInFormatError](/reference/Func/AddInFormatError)
---
