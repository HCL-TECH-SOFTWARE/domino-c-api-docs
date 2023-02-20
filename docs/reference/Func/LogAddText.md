##### Function : Log
##### LogAddText - Add a text item to a log entry.
---
```
#include <log.h>
STATUS LNVARARGS LogAddText(

	WORD  LogEntry,
	WORD  Flags,
	char far *ItemName,
	HMODULE  hModule,
	STATUS  Message,
	char far *FormatString,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

This function takes a log entry number, a lock entry flag, the name of the 
item, the handle of the module containing the string table you wish to use, the 
STATUS code of the message you wish to load from the string table, a string 
containing a printf style format specifier, and up to 6 format-specifier 
arguments.  Any pointer values passed as one of these arguments must be a far 
pointer.  The print format specifiers supported by Domino are described in the 
Tech Note "Domino Print Format Specifiers".  Tech Notes are listed in the view, 
Reference Tools/Tech Notes.

The string resulting from the combination of the specifier string and the 
corresponding arguments will be appended to the log entry as an item of 
TYPE_TEXT.  If the log entry already contains a text item with the same name, 
this function will append a carriage return ('\r'),  before appending the new 
value.  The STATUS code causes the appropriate message to be loaded from the 
module's string table.

**Parameters :**
Input :
LogEntry  -  A WORD containing the number of the log entry to use.

Flags  -  A WORD flag that determines how often the log entry is flushed to disk.  If LOG_LEAVE_LOCKED is specified, then the log entry is not written to disk until it is completed, to preseve the consistency of the fields in the entry.  If 0 is specified (the default), then the partially completed log entry is flushed to disk every so often so that it can be seen in the Log database.  See LOG_xxx for additional flags.

ItemName  -  A null-terminated item name of the item to be added.

hModule  -  The HMODULE of the executable whose string table should be searched for the "Message" argument (argument 5).  This value is usually obtained from the first argument of a call to AddInMain, which is the wrapper function used in Lotus Domino Server add-in applications.  If you wish, you may use the value returned by the native operating or run-time system calls.  A value of NULLHANDLE may be used instead, indicating that the Domino string table should be searched.

Message  -  A STATUS code of an error or message.  Use NOERROR if there is no error condition associated with the message.

FormatString  -  A text string containing a 'C' Language printf format string. The string may contain printf-type (%) format specifiers.  For each format specifier provided, there should be an additional argument provided for formatting into the log entry item.  A character string with no format specifiers may also be used.

optional_var1, ...  -  From 0 to 24 bytes of arguments of any type, each corresponding to one of the format specifiers embedded in the string loaded by the first argument.  All pointer values must be "far".  Leave off these parameters entirely if there are no format specifiers in the format string.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added text to log entry.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.



**Sample Usage :**
```

    sprintf(item_name,"%s", "TextBody");
    if (error_status = LogAddText(log_entry, LOG_LEAVE_LOCKED,
                            item_name,
                            NULLHANDLE, 0,
                            "%s", (char far *) log_entry_body))
       goto Exit;
```
**See Also :**
[LogCreateEntry](/reference/Func/LogCreateEntry)
[LogAddNumberItem](/reference/Func/LogAddNumberItem)
[LogAddTextlistItem](/reference/Func/LogAddTextlistItem)
[LogAddTimeItem](/reference/Func/LogAddTimeItem)
[LogCompleteEntry](/reference/Func/LogCompleteEntry)
---
