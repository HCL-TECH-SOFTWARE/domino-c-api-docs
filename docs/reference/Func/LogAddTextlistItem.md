##### Function : Log
##### LogAddTextlistItem - Add text to a text list in a log entry.
---
```
#include <log.h>
STATUS LNPUBLIC LogAddTextlistItem(

	WORD  LogEntry,
	WORD  Flags,
	char far *ItemName,
	char far *Text);
```
**Description :**

This function takes a log entry number, a lock entry flag, the name of the text 
list item,  and a null-terminated string.  It appends the string as the next 
entry in the named text list.  If there is no text list item by that name, the 
function creates one and then adds the string as the first entry in the list.  

Please note that if you determine at some point in your algorithm that you 
would like to change the contents of the text list item, the only means at your 
disposal is the complete destruction of the log entry via LogCloseEntry.  The 
log entry enables you to record selected data from a chronologically ordered 
stream of events, it should not be looked upon as a database record whose 
contents are completely modifiable at any time.  You may wish to create other 
types of notes in your application's database to provide that capability.

**Parameters :**
Input :
LogEntry  -  A WORD containing the number of the log entry to use.

Flags  -  A WORD flag that determines how often the log entry is flushed to disk.  If LOG_LEAVE_LOCKED is specified, then the log entry is not written to disk until it is completed, to preseve the consistency of the fields in the entry.  If 0 is specified (the default), then the partially completed log entry is flushed to disk every so often so that it can be seen in the Log database.

ItemName  -  A null-terminated item name of the item to be added.

Text  -  A pointer to a null-terminated text string containing the text you wish to add to the text list.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added text to text list in log entry.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.



**Sample Usage :**
```
/* Add a Text List Item to the AddinEvent form */
 
sprintf(item_name, "%s", "AddInEvents");
AddInFormatError(error_msg, MSG_SMKADDN_NAMESTUB,
                    "Creating Task Statistics");
if (error_status = LogAddTextlistItem(log_entry,
                                    LOG_LEAVE_LOCKED, item_name,
                                    error_msg))
   goto Exit;
```
**See Also :**
[LogAddNumberItem](/domino-c-api-docs/reference/Func/LogAddNumberItem)
[LogAddText](/domino-c-api-docs/reference/Func/LogAddText)
[LogAddTimeItem](/domino-c-api-docs/reference/Func/LogAddTimeItem)
[LogCompleteEntry](/domino-c-api-docs/reference/Func/LogCompleteEntry)
[LogCreateEntry](/domino-c-api-docs/reference/Func/LogCreateEntry)
---
