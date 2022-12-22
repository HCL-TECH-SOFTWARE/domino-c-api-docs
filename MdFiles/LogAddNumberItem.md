




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



**LogAddNumberItem** **- Add a
number to a log entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNPUBLIC **LogAddNumberItem(**  

      WORD  LogEntry,  

      WORD  Flags,  

      char far \*ItemName,  

      NUMBER far \*Number**);**



**Description :**



This function
takes a log entry number,  a lock entry flag, the name of the item, and the
NUMBER value you wish to add to the log entry.  It deletes any existing item
with the same name before adding the new value.


 


**Parameters :**



Input :  

LogEntry  -  A WORD containing the number of the log entry to use.  

  

Flags  -  A WORD flag that determines how often the log entry is flushed to
disk.  If LOG\_LEAVE\_LOCKED is specified, then the log entry is not written to
disk until it is completed, to preseve the consistency of the fields in the
entry.  If 0 is specified (the default), then the partially completed log entry
is flushed to disk every so often so that it can be seen in the Log database.  

  

ItemName  -  A null-terminated item name of the item to be added.  

  

Number  -  A pointer to a NUMBER containing the number you wish to append to
the log entry.  The Domino typedefs FLOAT and NUMBER,  are synonymous with the
standard 'C' language type 'double'.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added number to log entry.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and display
the error for the user.  

  

  




 **Sample Usage :**


  

   if (error\_status = LogAddNumberItem(log\_entry, LOG\_LEAVE\_LOCKED,  

                         "DaysExecuted", (NUMBER \*) &day\_double))  

       goto Exit;


 **See Also :**


**[LogCreateEntry](LogCreateEntry.md)**


**[LogAddText](LogAddText.md)**


**[LogAddTextlistItem](LogAddTextlistItem.md)**


**[LogAddTimeItem](LogAddTimeItem.md)**


**[LogCompleteEntry](LogCompleteEntry.md)**



----------------------------------------------------------------------------------------------------------


 





