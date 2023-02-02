##### Function : AddIn
##### AddInLogMsg - Format and write a message to the log file (uses string resources).
---
##### #include <addin.h>
void LNPUBLIC **AddInLogMsg(**

	STATUS  StringID,
	char far *Arg);
**Description :**
AddInLogMsg formats an error message, displays it on the standard output, and 
appends the message as new line to the "Events" field in a Miscellaneous Events 
document in the  Domino server or Notes client log.  The generated message has 
the form:
 
          <DATE>  <TIME> <status message>

The first parameter, StringID, is a resource ID. It must identify a string 
resource located in the calling program's resource module. The string specified 
by StringID may contain one printf-type format specifier. If it does, the 
second parameter, Arg, must point to a printf-type argument that resolves the 
format specifier.  Only one format specifier argument is supported in this 
function.  Use AddInLogMessage if more than one format specifier argument is 
needed.  The print format specifiers supported by Domino are described in the 
TechNote "Domino Print Format Specifiers".
Use AddInLogMsg to log events that are not associated with a STATUS code 
returned from a C API function. AddInLogMsg is a macro that calls AddInLogError:

     #define AddInLogMsg(s, e) AddInLogError(s, NOERROR, e)

 AddInLogMsg may be called from a NotesMain, main, or AddInMain API program. 

When using this function, you should call either AddInIdle or AddInIdleDelay on 
a regular basis to flush the log entries from memory to disk and free up the 
memory.
**Parameters :**
Input :
StringID  -  Resource ID of string to be formatted.  The string may contain up to one printf-type (%) format specifier.  If a format specifier is present, a second argument must be provided for formatting into the message string.

Arg  -  Pointer to an argument to be formatted into the  printf-type (%) format specifier in the string specified by StringID.  Specify NULL if the string contains no format specifier.

Output :
(routine)  -  None


**Sample Usage :**
```
/* #define MSG_SMKADDN_STARTED                     (PKG_ADDIN+11)    */
/*    msgtext(MSG_SMKADDN_STARTED, "Smoke Addin Example Started up") */
   
/* Log the task status: message appears on console display and  */
/* in Miscellaneous "Events" View in the server's LOG.NSF       */

AddInLogMsg(MSG_SMKADDN_STARTED);
```
**See Also :**
[AddInLogError](D:/md_files/AddInLogError.md)
[AddInLogMessage](D:/md_files/AddInLogMessage.md)
[AddInSetStatus](D:/md_files/AddInSetStatus.md)
[AddInFormatError](D:/md_files/AddInFormatError.md)
[LogEvent](D:/md_files/LogEvent.md)
---
