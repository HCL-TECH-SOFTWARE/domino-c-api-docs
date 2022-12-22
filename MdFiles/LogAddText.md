




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Log**



**LogAddText** **- Add a
text item to a log entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNVARARGS **LogAddText(**  

      WORD  LogEntry,  

      WORD  Flags,  

      char far \*ItemName,  

      HMODULE  hModule,  

      STATUS  Message,  

      char far \*FormatString,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



This
function takes a log entry number, a lock entry flag, the name of the item, the
handle of the module containing the string table you wish to use, the STATUS
code of the message you wish to load from the string table, a string containing
a printf style format specifier, and up to 6 format-specifier arguments.  Any
pointer values passed as one of these arguments must be a far pointer.  The
print format specifiers supported by Domino are described in the Tech Note
"[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BF500155DA9)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.


 


The string
resulting from the combination of the specifier string and the corresponding
arguments will be appended to the log entry as an item of TYPE\_TEXT.  If the
log entry already contains a text item with the same name, this function will
append a carriage return ('\r'),  before appending the new value.  The STATUS
code causes the appropriate message to be loaded from the module's string
table.


 


**Parameters :**



Input :  

LogEntry  -  A WORD containing the number of the log entry to use.  

  

Flags  -  A WORD flag that determines how often the log entry is flushed to
disk.  If LOG\_LEAVE\_LOCKED is specified, then the log entry is not written to
disk until it is completed, to preseve the consistency of the fields in the
entry.  If 0 is specified (the default), then the partially completed log entry
is flushed to disk every so often so that it can be seen in the Log database. 
See LOG\_xxx for additional flags.  

  

ItemName  -  A null-terminated item name of the item to be added.  

  

hModule  -  The HMODULE of the executable whose string table should be searched
for the "Message" argument (argument 5).  This value is usually
obtained from the first argument of a call to AddInMain, which is the wrapper
function used in Lotus Domino Server add-in applications.  If you wish, you may
use the value returned by the native operating or run-time system calls.  A
value of NULLHANDLE may be used instead, indicating that the Domino string
table should be searched.  

  

Message  -  A STATUS code of an error or message.  Use NOERROR if there is no
error condition associated with the message.  

  

FormatString  -  A text string containing a 'C' Language printf format string.
The string may contain printf-type (%) format specifiers.  For each format
specifier provided, there should be an additional argument provided for
formatting into the log entry item.  A character string with no format
specifiers may also be used.  

  

optional\_var1, ...  -  From 0 to 24 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the string loaded by
the first argument.  All pointer values must be "far".  Leave off
these parameters entirely if there are no format specifiers in the format
string.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added text to log entry.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and display
the error for the user.  

  

  




 **Sample Usage :**


  

    sprintf(item\_name,"%s", "TextBody");  

    if (error\_status = LogAddText(log\_entry, LOG\_LEAVE\_LOCKED,  

                            item\_name,  

                            NULLHANDLE, 0,  

                            "%s", (char far \*) log\_entry\_body))  

       goto Exit;


 **See Also :**


**[LogCreateEntry](LogCreateEntry.md)**


**[LogAddNumberItem](LogAddNumberItem.md)**


**[LogAddTextlistItem](LogAddTextlistItem.md)**


**[LogAddTimeItem](LogAddTimeItem.md)**


**[LogCompleteEntry](LogCompleteEntry.md)**



----------------------------------------------------------------------------------------------------------


 





