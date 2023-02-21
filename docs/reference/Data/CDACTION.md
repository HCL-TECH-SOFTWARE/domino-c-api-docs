##### Data Type : Composite Data
##### CDACTION - Record defining a custom menu action on a form or view.
---
```
#include <actods.h>
```
**Description :**

The designer of a form or view may define custom actions associated with that 
form or view.  Actions may be presented to the user as buttons on the action 
button bar or as options on the "Actions" menu.

R5 supports new action types that can not be stored in a manner that is 
backwards compatible.  New, incompatible action data is stored in the  
"$V5ACTIONS" rich-text item.  Action data that is compatible with R4 is stored 
in the "$ACTIONS" rich-text item.  It is common for both items to be present, 
allowing R5-only actions to be added while still allowing compatible actions to 
be visible in R4.

The first set of records in this item is usually a CDACTIONBAR record and a 
CDACTIONBAREXT record containing the attributes for displaying the action 
button bar.  That set of records is followed by CDACTION records containing the 
definitions for each custom action.

The order in which the CDACTION records are stored determines the order in 
which the buttons and entries on the "Actions" pull-down menu will be displayed.

The fields in this structure are:

Header	Identifies this as a CDACTION record.
Type	Type of action (see ACTION_xxx (type)).
IconIndex	Index into the icon list.
Flags	Flag values for this action (see ACTION_xxx (flags)).
TitleLen	Length of the action's title.
FormulaLen	Length of the "hide when" formula.  Note that this is NOT the 
length of the action formula if the type for this action is ACTION_RUN_FORMULA.
ShareId	ID of the Shared Action

This record is followed by the title for the action (which may be padded to 
occupy an even number of bytes), the action data, and, optionally, a "hide 
when" formula.  The number of bytes of action data is Header.Length - TitleLen 
- FormulaLen.

The "Flags" field determines when and where this action will be presented to 
the user.  The Flags field may contain any combination of the ACTION_xxx values.

The action may be one of the following:

*  Invoke a system command, identified by a four-byte code
*  Run a formula
*  Run Lotus Script
*  Run Java Script
*  Invoke Domino actions (see the CDACTIONxxx records)

The format of the action data for the CDACTION record depends on the Type code:

ACTION_RUN_FORMULA:  The action data consists of a compiled Domino formula.  
(Note that a CDACTION record can also contain a "hide when" formula, if 
ACTION_NO_FORMULA is not set and the FormulaLen field is non-zero.  Such a 
record will contain action data consisting of a formula followed by the "hide 
when" formula.)

ACTION_RUN_SCRIPT:  The action data consists of Lotus Script source code 
(unless the script has been stored without the source code).
If the data for a Lotus Script action is too large to fit into a single Domino 
item, a new item will be created.  The item containing the source will be named 
"$$ACTSRC_", followed by an index number, and the item containing the object 
code will be named "$SCRIPTOBJ_" followed by the index number.

ACTION_RUN_AGENT:  The action data consists of Domino agent action records 
(records such as CDACTIONBYFORM, CDACTIONDBCOPY,  ... , CDACTIONSENDMAIL);  the 
total size of all the agent action records is included in the size of the 
CDACTION record.

ACTION_OLDSYS_COMMAND, ACTION_SYS_COMMAND:  The action data consists of two 
WORD values (4 bytes total).  In R4, the first WORD identifies a standard 
system command by an index number, while in R5, the first WORD is the index of 
the command in the list of actions (starting with 1).  In both cases, the 
second WORD is a command code identifying the system action.  Please see the 
Tech Note "System Action Command Codes" for more details.

ACTION_RUN_JAVASCRIPT:  The CDACTION record is followed by one CDEVENT record 
and one or more CDBLOBPART records.  The CDEVENT record contains a DWORD that 
holds the size of the JavaScript code, and each CDBLOBPART record contains a 
WORD that indicates how much of the code is included in this given blob.  Loop 
through all the CDBLOBPART records followed to read in all the JavaScript code.

**See Also :**
[ACTION_SYS_CMD_xxx](/domino-c-api-docs/reference/Symb/ACTION_SYS_CMD_xxx)
[ACTION_xxx (flags)](/domino-c-api-docs/reference/Symb/ACTION_xxx (flags))
[ACTION_xxx (type)](/domino-c-api-docs/reference/Symb/ACTION_xxx (type))
[CDACTIONBYFORM](/domino-c-api-docs/reference/Data/CDACTIONBYFORM)
[CDACTIONDBCOPY](/domino-c-api-docs/reference/Data/CDACTIONDBCOPY)
[CDACTIONDELETE](/domino-c-api-docs/reference/Data/CDACTIONDELETE)
[CDACTIONFOLDER](/domino-c-api-docs/reference/Data/CDACTIONFOLDER)
[CDACTIONFORMULA](/domino-c-api-docs/reference/Data/CDACTIONFORMULA)
[CDACTIONHEADER](/domino-c-api-docs/reference/Data/CDACTIONHEADER)
[CDACTIONLOTUSSCRIPT](/domino-c-api-docs/reference/Data/CDACTIONLOTUSSCRIPT)
[CDACTIONMODIFYFIELD](/domino-c-api-docs/reference/Data/CDACTIONMODIFYFIELD)
[CDACTIONNEWSLETTER](/domino-c-api-docs/reference/Data/CDACTIONNEWSLETTER)
[CDACTIONREADMARKS](/domino-c-api-docs/reference/Data/CDACTIONREADMARKS)
[CDACTIONREPLY](/domino-c-api-docs/reference/Data/CDACTIONREPLY)
[CDACTIONRUNAGENT](/domino-c-api-docs/reference/Data/CDACTIONRUNAGENT)
[CDACTIONSENDDOCUMENT](/domino-c-api-docs/reference/Data/CDACTIONSENDDOCUMENT)
[CDACTIONSENDMAIL](/domino-c-api-docs/reference/Data/CDACTIONSENDMAIL)
---
