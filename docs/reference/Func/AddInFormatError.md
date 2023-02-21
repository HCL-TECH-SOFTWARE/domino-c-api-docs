##### Function : AddIn
##### AddInFormatError - Format an error string (uses string resources).
---
```
#include <addin.h>
void LNVARARGS AddInFormatError(

	char far *retString,
	STATUS  StringID,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

AddInFormatError is used to generate a formatted error message.  The message 
can then be used by the program for purposes other than standard AddIn logging, 
for example, updating the status display (see AddInSetStatus).  

It can also be used to format error messages that require more than one 
argument for its format string.  In this case, the formatted error string can 
then be passed to AddInLogError as the Arg parameter, with a string resource id 
that is associated with a text string containing a "%s" format specifier passed 
in as the StringID parameter.  However, the function, AddInLogMessage, provides 
an easier way to accomplish this.

The second parameter, StringID,  is a resource ID that identifies a string 
resource located in the calling program's resource module.  The string 
specified by StringID may contain up to four printf-type format specifiers.  If 
it does contain printf-type format specifiers, the remaining parameters must be 
printf-type arguments that resolve each of the format specifiers.  Up to 16 
bytes of additional parameters may be specified.  The print format specifiers 
supported by Domino are described in the Tech Note. "Domino Print Format 
Specifiers". Tech Notes are listed in the view, Reference Tools/Tech Notes.
  
This function performs a function similiar to "sprintf", except that it works 
with Domino string resources.

This routine only supports errors that are stored as string resources and 
therefore is not portable across all types of platforms.  Use the function, 
AddInFormatErrorText for platforms that do not support string resources.

**Parameters :**
Input :

StringID  -  Resource ID of string to be formatted. The string may contain up to four printf-type (%) format specifiers. For each format specifier provided, there should be an additional argument provided for formatting into the message string.

optional_var1, ...  -  From 0 to 16 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the format string associated with the StringID argument.  All pointer values must be "far". Leave off this parameter entirely (use only the above 2 arguments) if there are no format specifiers in the format string.

Output :
(routine)  -  None.


retString  -  The formatted message string is placed in the specified character buffer.  It is the caller's responsibility to allocate this buffer (MAXSPRINTF bytes) prior to making the call.


**Sample Usage :**
```

            /* Create a 3 string arg error_msg from 3 numeric values*/
            sprintf(scratch_str1, "%lf", day_double);
            sprintf(scratch_str2, "%lf", min_double);
            sprintf(scratch_str3, "%lf", sec_double/20.0);
            AddInFormatError(error_msg, MSG_SMKADDN_STATS,
                            scratch_str1, scratch_str2, scratch_str3);
            AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
  
```
**See Also :**
[AddInLogError](/domino-c-api-docs/reference/Func/AddInLogError)
[AddInSetStatus](/domino-c-api-docs/reference/Func/AddInSetStatus)
[AddInLogMsg](/domino-c-api-docs/reference/Func/AddInLogMsg)
[AddInLogMessage](/domino-c-api-docs/reference/Func/AddInLogMessage)
[AddInFormatErrorText](/domino-c-api-docs/reference/Func/AddInFormatErrorText)
---
