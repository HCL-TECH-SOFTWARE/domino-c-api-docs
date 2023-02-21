##### Function : Log
##### LogEvent - Log an AddIn event in the Domino Server or Notes client log database.
---
```
#include <log.h>
STATUS LNVARARGS LogEvent(

	STATUS  StringID,
	HMODULE  hModule,
	STATUS  AdditionalErrorCode,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

This function formats an error message, displays it on the standard output, and 
enters it in the Domino Server or Notes client log database.  The generated 
message has the form:
 
          <DATE>  <TIME>  <Primary status message>: <Secondary status message>

LogEvent is similar to AddInLogError but more flexible.  LogEvent uses the 
second argument, "hModule", to resolve "AdditionalErrorCode".  If 
"AdditionalErrorCode" is a STATUS returned from a C API function or a string in 
the calling program's resource module, then use AddInLogError.  Otherwise, if 
the string resource "AdditionalErrorCode" is located in a non-standard module, 
use LogEvent.

The first parameter, "StringID", identifies a string in the calling program's 
string table.  The message string may contain printf-type (%) format 
specifiers.  For each format specifier provided, there should be an additional 
argument provided for output, starting with the fourth argument.  The print 
format specifiers supported by Domino are described in the Tech Note "Domino 
Print Format Specifiers".  Tech Notes are listed in the view, Reference 
Tools/Tech Notes.  The third parameter, "AdditionalErrorCode", may be another 
string resource ID, or it may be the STATUS returned from a C API function. The 
second parameter, "hModule", specified where "AdditionalErrorCode" is 
resolved.  You may specify NULLHANDLE for the second parameter if 
"AdditionalErrorCode" is resolved by Domino or by the calling program.

When using this function, you should call either AddInIdle or AddInIdleDelay on 
a regular basis to flush the log entries from memory to disk and free up the 
memory.

**Parameters :**
Input :
StringID  -  STATUS code for the desired string resource.

hModule  -  A module handle of the module containing the string resources.

AdditionalErrorCode  -  A STATUS code to return.  If you choose not to supply an error_status, a value of NOERROR is an acceptable argument.

optional_var1, ...  -  From 0 to 24 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the string loaded by the first argument.  All pointer values must be "far".  Leave off this parameter entirely (use only the above 3 arguments) if there are no format specifiers in the format string.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully logged the event.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```
/* Add an Log Entry to the Events item in the current Misc-   */
/* ellaneous Events Note being built for LOG.NSF.             */
/* Echo same text with time/date prefix to Server Console.    */
/* This Log API is the functional equivalent the following    */
/* AddIn APIs: AddInLogError and AddInLogMsg. It is up to you */
/* whether or not to mix the packages together in an AddIn App*/

if (error_status = LogEvent(MSG_SMKADDN_SHUTDOWN,
                          hModule, NOERROR,
                          (char far *) log_entry_farewell))
   goto Exit;
```
**See Also :**
[AddInFormatError](/domino-c-api-docs/reference/Func/AddInFormatError)
[AddInLogError](/domino-c-api-docs/reference/Func/AddInLogError)
[LogCloseEntry](/domino-c-api-docs/reference/Func/LogCloseEntry)
[LogCompleteEntry](/domino-c-api-docs/reference/Func/LogCompleteEntry)
[LogCreateEntry](/domino-c-api-docs/reference/Func/LogCreateEntry)
---
