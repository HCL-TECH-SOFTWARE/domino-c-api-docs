




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.5**



**Data Type : Composite Data; Form;
Rich Text**



**CDACTION** **-** Record
defining a custom menu action on a form or view.


**----------------------------------------------------------------------------------------------------------**



**#include
<actods.h>**



**Definition :**



typedef struct {  

   LSIG  Header;    /\* Signature and Length \*/  

   WORD  Type;      /\* Type of action (formula, script, etc.) \*/  

   WORD  IconIndex; /\* Index into array of icons \*/  

   DWORD Flags;     /\* Action flags \*/  

   WORD  TitleLen;  /\* Length (in bytes) of action's title \*/  

   WORD  FormulaLen;/\* Length (in bytes) of "hide when" formula \*/  

   DWORD ShareId;   /\* Share ID of the Shared Action \*/


/\* Variable portion of
the record:


        TitleLen bytes
of action's title


        Action data: 
(Header.Length - TitleLen - FormulaLen) bytes


         of formula,
script, etc.


        FormulaLen
bytes of "hide when" formula \*/


} CDACTION;


 


**Description :**



The designer
of a form or view may define custom actions associated with that form or view. 
Actions may be presented to the user as buttons on the action button bar or as
options on the "Actions" menu.


 


R5 supports
new action types that can not be stored in a manner that is backwards
compatible.  New, incompatible action data is stored in the  "**$V5ACTIONS**"
rich-text item.  Action data that is compatible with R4 is stored in the "**$ACTIONS**"
rich-text item.  It is common for both items to be present, allowing R5-only
actions to be added while still allowing compatible actions to be visible in
R4.


 


The first
set of records in this item is usually a **CDACTIONBAR** record and a **CDACTIONBAREXT** record
containing the attributes for displaying the action button bar.  That set of
records is followed by **CDACTION** records containing the definitions
for each custom action.


 


The order in
which the CDACTION records are stored determines the order in which the buttons
and entries on the "Actions" pull-down menu will be displayed.


 


The fields
in this structure are:


 


**Header**            Identifies
this as a CDACTION record.


**Type**                Type
of action (see ACTION\_xxx (type)).


**IconIndex**      Index
into the icon list.


**Flags**              Flag
values for this action (see ACTION\_xxx (flags)).


**TitleLen**        Length
of the action's title.


**FormulaLen**    Length
of the "hide when" formula.  Note that this is NOT the length of the
action formula if the type for this action is ACTION\_RUN\_FORMULA.


**ShareId**          ID
of the Shared Action


 


This record
is followed by the title for the action (which may be padded to occupy an even
number of bytes), the action data, and, optionally, a "hide when"
formula.  The number of bytes of action data is Header.Length - TitleLen -
FormulaLen.


 


The
"Flags" field determines when and where this action will be presented
to the user.  The Flags field may contain any combination of the ACTION\_xxx
values.


 


The action
may be one of the following:


 


\*  Invoke a
system command, identified by a four-byte code


\*  Run a
formula


\*  Run Lotus
Script


\*  Run Java
Script


\*  Invoke
Domino actions (see the CDACTIONxxx records)


 


The format
of the action data for the CDACTION record depends on the Type code:


 


**ACTION\_RUN\_FORMULA**:  The
action data consists of a compiled Domino formula.  (Note that a CDACTION
record can also contain a "hide when" formula, if ACTION\_NO\_FORMULA is
not set and the FormulaLen field is non-zero.  Such a record will contain
action data consisting of a formula followed by the "hide when"
formula.)


 


**ACTION\_RUN\_SCRIPT**:  The
action data consists of Lotus Script source code (unless the script has been
stored without the source code).


If the data
for a Lotus Script action is too large to fit into a single Domino item, a new
item will be created.  The item containing the source will be named
"$$ACTSRC\_", followed by an index number, and the item containing the
object code will be named "$SCRIPTOBJ\_" followed by the index number.


 


**ACTION\_RUN\_AGENT**:  The
action data consists of Domino agent action records (records such as
CDACTIONBYFORM, CDACTIONDBCOPY,  ... , CDACTIONSENDMAIL);  the total size of
all the agent action records is included in the size of the CDACTION record.


 


**ACTION\_OLDSYS\_COMMAND**, **ACTION\_SYS\_COMMAND**:  The
action data consists of two WORD values (4 bytes total).  In R4, the first WORD
identifies a standard system command by an index number, while in R5, the first
WORD is the index of the command in the list of actions (starting with 1).  In
both cases, the second WORD is a command code identifying the system action. 
Please see the Tech Note "[System Action Command Codes](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EAD69A082854DA32852569DD00446DCC)" for more
details.


 


**ACTION\_RUN\_JAVASCRIPT**:  The
CDACTION record is followed by one CDEVENT record and one or more CDBLOBPART
records.  The CDEVENT record contains a DWORD that holds the size of the
JavaScript code, and each CDBLOBPART record contains a WORD that indicates how
much of the code is included in this given blob.  Loop through all the
CDBLOBPART records followed to read in all the JavaScript code.


 **See Also :**


**[ACTION\_SYS\_CMD\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EAD69A082854DA32852569DD00446DCC)**


**[ACTION\_xxx (flags)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/58250FD43C78A3AD852566760051A3DE)**


**[ACTION\_xxx (type)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7BF89CD0DA4C5A0D85256677003F1A20)**


**[CDACTIONBYFORM](CDACTIONBYFORM.md)**


**[CDACTIONDBCOPY](CDACTIONDBCOPY.md)**


**[CDACTIONDELETE](CDACTIONDELETE.md)**


**[CDACTIONFOLDER](CDACTIONFOLDER.md)**


**[CDACTIONFORMULA](CDACTIONFORMULA.md)**


**[CDACTIONHEADER](CDACTIONHEADER.md)**


**[CDACTIONLOTUSSCRIPT](CDACTIONLOTUSSCRIPT.md)**


**[CDACTIONMODIFYFIELD](CDACTIONMODIFYFIELD.md)**


**[CDACTIONNEWSLETTER](CDACTIONNEWSLETTER.md)**


**[CDACTIONREADMARKS](CDACTIONREADMARKS.md)**


**[CDACTIONREPLY](CDACTIONREPLY.md)**


**[CDACTIONRUNAGENT](CDACTIONRUNAGENT.md)**


**[CDACTIONSENDDOCUMENT](CDACTIONSENDDOCUMENT.md)**


**[CDACTIONSENDMAIL](CDACTIONSENDMAIL.md)**



----------------------------------------------------------------------------------------------------------


 





