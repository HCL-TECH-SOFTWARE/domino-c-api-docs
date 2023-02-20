##### Function : Log
##### LogCreateEntry - Create a new log entry.
---
```
#include <log.h>
STATUS LNPUBLIC LogCreateEntry(

	char far *FormName,
	WORD far *retLogEntry);
```
**Description :**

This function creates a new entry in the Domino Server or Notes client log 
file.  It sets the "StartTime" field to the current  time/date, the "Form" 
field to the specified form name, and the "Server" field to the current server 
name. It returns the LogEntry ID number required by other functions in the Log 
Package. 

LogCreateEntry adds a new document to the log file, unlike AddinLogMessage 
which adds a message to the current Events document.  LogCreateEntry lets you 
create documents in the log file for exclusive use by your program.  Specify a 
"Form" of your own design with the form_name argument.  Set fields of type text 
by calling LogAddText, text list by calling LogAddTextlistItem, time by calling 
LogAddTimeItem, and number by calling LogAddNumberItem.

Call LogCompleteEntry to set the current time/date in the "FinishTime" field, 
save the document in the log file, and deallocate the LogEntry. 

Note: You must deallocate the log entry by calling LogCloseEntry or 
LogCompleteEntry when finished.

LogCreateEntry may be called from a NotesMain, main, or AddInMain API program.

**Parameters :**
Input :
FormName  -  A pointer to a text buffer containing the name of the 'form' in the LOG.NSF database that you would like to use while composing this log entry.  It must be a null-terminated string.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully created a log entry.

ERR_LOG_NULLHANDLE - LogEntry not allocated. This status is returned if the Lotus Domino Server software is not currently running.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.


retLogEntry  -  The address of a WORD in which the log entry ID number is returned.  This number is used by other functions in the Log Package to reference the log entry. 


**Sample Usage :**
```
if (error_status = LogCreateEntry(form_name, &log_entry))
   goto Exit;
else
   cleanup_state += COMPLETE_LOG_ENTRY;

/* NOTE: LogCreateEntry() automatically fills in the "Server",  */
/* "StartTime" & "Form" fields/items for you.                   */
```
**See Also :**
[LogAddNumberItem](/reference/Func/LogAddNumberItem)
[LogAddText](/reference/Func/LogAddText)
[LogAddTextlistItem](/reference/Func/LogAddTextlistItem)
[LogAddTimeItem](/reference/Func/LogAddTimeItem)
[LogCloseEntry](/reference/Func/LogCloseEntry)
[LogCompleteEntry](/reference/Func/LogCompleteEntry)
---
