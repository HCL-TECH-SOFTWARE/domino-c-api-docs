##### Function : Mail Gateway
##### MailLogEvent - Add an event to the mail logs using a string resource.
---
```
#include <mailserv.h>
STATUS LNVARARGS MailLogEvent(

	WORD  Flags,
	STATUS  StringID,
	HMODULE  hModule,
	STATUS  AdditionalErrorCode,
	<Any 'C' type>  [optional arguments]...);
```
**Description :**

Log a mail gateway event.  The "Flags" parameter controls which logs will be 
used;  for details, see the entry MAIL_LOG_xxx.  The StringID identifies a 
string resource in the module specified by hModule.  This string may contain 
printf-type % format specifiers.  The print format specifiers supported by 
Domino are described in the Tech Note "Domino Print Format Specifiers".  Tech 
Notes are listed in the view, Reference Tools/Tech Notes.  The parameter 
AdditionalErrorCode is used to select a secondary status message string which 
is appended to the log message.

This function formats an error message, displays it on the standard output, and 
enters it in the selected logs.  The generated message has the form:
 
          <DATE>  <TIME>  <Primary status message>: <Secondary status message>

When using this function, you should call either AddInIdle or AddInIdleDelay on 
a regular basis to flush the log entries from memory to disk and free up the 
memory.

**Parameters :**
Input :
Flags  -  Mail logging control flags.  See the entry MAIL_LOG_xxx for details.

StringID  -  STATUS code or resource ID for the desired string resource.  The message string may contain printf-type (%) format specifiers.  For each format specifier provided, there should be an additional argument provided for output, starting with the fifth argument.

hModule  -  A module handle of the module containing the string resources.

AdditionalErrorCode  -  A STATUS code to return to the Server.  If there is no additional status information, a value of NOERROR is an acceptable argument.

[optional arguments]...  -  From 0 to 24 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the string loaded by the second argument.  All pointer values must be "far".  Leave off this parameter entirely (use only the above 4 arguments) if there are no format specifiers in the format string.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Log message recorded.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 



**See Also :**
[LogEvent](/domino-c-api-docs/reference/Func/LogEvent)
[MailLogEventText](/domino-c-api-docs/reference/Func/MailLogEventText)
[MAIL_LOG_xxx](/domino-c-api-docs/reference/Symb/MAIL_LOG_xxx)
---
