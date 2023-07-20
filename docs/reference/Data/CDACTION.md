##### Data Type : Composite Data
##### CDACTION - Record defining a custom menu action on a form or view.
---
```
#include <actods.h>
```

**Definition :**
```
typedef struct {
   LSIG  Header;    /* Signature and Length */
   WORD  Type;      /* Type of action (formula, script, etc.) */
   WORD  IconIndex; /* Index into array of icons */
   DWORD Flags;     /* Action flags */
   WORD  TitleLen;  /* Length (in bytes) of action's title */
   WORD  FormulaLen;/* Length (in bytes) of "hide when" formula */
   DWORD ShareId;   /* Share ID of the Shared Action */
/* Variable portion of the record:
        TitleLen bytes of action's title
        Action data:  (Header.Length - TitleLen - FormulaLen) bytes
         of formula, script, etc.
        FormulaLen bytes of "hide when" formula */
} CDACTION;
```

**Description :**

The designer of a form or view may define custom actions associated with that form or view.  Actions may be presented to the user as buttons on the action button bar or as options on the &quot;Actions&quot; menu.
<ul><br>
<br>
R5 supports new action types that can not be stored in a manner that is backwards compatible.  New, incompatible action data is stored in the  &quot;<tt><b>$V5ACTIONS</b></tt>&quot; rich-text item.  Action data that is compatible with R4 is stored in the &quot;<tt><b>$ACTIONS</b></tt>&quot; rich-text item.  It is common for both items to be present, allowing R5-only actions to be added while still allowing compatible actions to be visible in R4.<br>
<br>
The first set of records in this item is usually a <tt><b>CDACTIONBAR</b></tt> record and a <tt><b>CDACTIONBAREXT</b></tt> record containing the attributes for displaying the action button bar.  That set of records is followed by <tt><b>CDACTION</b></tt> records containing the definitions for each custom action.<br>
<br>
The order in which the CDACTION records are stored determines the order in which the buttons and entries on the &quot;Actions&quot; pull-down menu will be displayed.<br>
<br>
The fields in this structure are:<br>
<br>
<tt><b>Header</b></tt>	Identifies this as a CDACTION record.<br>
<tt><b>Type</b></tt>	Type of action (see ACTION_xxx (type)).<br>
<tt><b>IconIndex</b></tt>	Index into the icon list.<br>
<tt><b>Flags</b></tt>	Flag values for this action (see ACTION_xxx (flags)).<br>
<tt><b>TitleLen</b></tt>	Length of the action's title.<br>
<tt><b>FormulaLen</b></tt>	Length of the &quot;hide when&quot; formula.  Note that this is NOT the length of the action formula if the type for this action is ACTION_RUN_FORMULA.<br>
<tt><b>ShareId</b></tt>	ID of the Shared Action<br>
<br>
This record is followed by the title for the action (which may be padded to occupy an even number of bytes), the action data, and, optionally, a &quot;hide when&quot; formula.  The number of bytes of action data is Header.Length - TitleLen - FormulaLen.<br>
<br>
The &quot;Flags&quot; field determines when and where this action will be presented to the user.  The Flags field may contain any combination of the ACTION_xxx values.<br>
<br>
The action may be one of the following:<br>
<br>
*  Invoke a system command, identified by a four-byte code<br>
*  Run a formula<br>
*  Run Lotus Script<br>
*  Run Java Script<br>
*  Invoke Domino actions (see the CDACTIONxxx records)<br>
<br>
The format of the action data for the CDACTION record depends on the Type code:<br>
<br>
<tt><b>ACTION_RUN_FORMULA</b></tt>:  The action data consists of a compiled Domino formula.  (Note that a CDACTION record can also contain a &quot;hide when&quot; formula, if ACTION_NO_FORMULA is not set and the FormulaLen field is non-zero.  Such a record will contain action data consisting of a formula followed by the &quot;hide when&quot; formula.)<br>
<br>
<tt><b>ACTION_RUN_SCRIPT</b></tt>:  The action data consists of Lotus Script source code (unless the script has been stored without the source code).<br>
If the data for a Lotus Script action is too large to fit into a single Domino item, a new item will be created.  The item containing the source will be named &quot;$$ACTSRC_&quot;, followed by an index number, and the item containing the object code will be named &quot;$SCRIPTOBJ_&quot; followed by the index number.<br>
<br>
<tt><b>ACTION_RUN_AGENT</b></tt>:  The action data consists of Domino agent action records (records such as CDACTIONBYFORM, CDACTIONDBCOPY,  ... , CDACTIONSENDMAIL);  the total size of all the agent action records is included in the size of the CDACTION record.<br>
<br>
<tt><b>ACTION_OLDSYS_COMMAND</b></tt>, <tt><b>ACTION_SYS_COMMAND</b></tt>:  The action data consists of two WORD values (4 bytes total).  In R4, the first WORD identifies a standard system command by an index number, while in R5, the first WORD is the index of the command in the list of actions (starting with 1).  In both cases, the second WORD is a command code identifying the system action.  Please see the Tech Note &quot;<a href="/apiref.nsf/61fd4e9848264ad28525620b006ba8bd/ead69a082854da32852569dd00446dcc?OpenDocument"><u><font color="#008000">System Action Command Codes</font></u></a>&quot; for more details.<br>
<br>
<tt><b>ACTION_RUN_JAVASCRIPT</b></tt>:  The CDACTION record is followed by one CDEVENT record and one or more CDBLOBPART records.  The CDEVENT record contains a DWORD that holds the size of the JavaScript code, and each CDBLOBPART record contains a WORD that indicates how much of the code is included in this given blob.  Loop through all the CDBLOBPART records followed to read in all the JavaScript code.</ul>



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
