




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



**LogAddTextlistItem** **- Add text
to a text list in a log entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNPUBLIC **LogAddTextlistItem(**  

      WORD  LogEntry,  

      WORD  Flags,  

      char far \*ItemName,  

      char far \*Text**);**



**Description :**



This function
takes a log entry number, a lock entry flag, the name of the text list item, 
and a null-terminated string.  It appends the string as the next entry in the
named text list.  If there is no text list item by that name, the function
creates one and then adds the string as the first entry in the list.    

  

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

  

Flags  -  A WORD flag that determines how often the log entry is flushed to
disk.  If LOG\_LEAVE\_LOCKED is specified, then the log entry is not written to
disk until it is completed, to preseve the consistency of the fields in the
entry.  If 0 is specified (the default), then the partially completed log entry
is flushed to disk every so often so that it can be seen in the Log database.  

  

ItemName  -  A null-terminated item name of the item to be added.  

  

Text  -  A pointer to a null-terminated text string containing the text you
wish to add to the text list.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added text to text list in log entry.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and display
the error for the user.  

  

  




 **Sample Usage :**


/\* Add a Text List Item
to the AddinEvent form \*/  

   

sprintf(item\_name, "%s", "AddInEvents");  

AddInFormatError(error\_msg, MSG\_SMKADDN\_NAMESTUB,  

                    "Creating Task Statistics");  

if (error\_status = LogAddTextlistItem(log\_entry,  

                                    LOG\_LEAVE\_LOCKED, item\_name,  

                                    error\_msg))  

   goto Exit;


 **See Also :**


**[LogAddNumberItem](LogAddNumberItem.md)**


**[LogAddText](LogAddText.md)**


**[LogAddTimeItem](LogAddTimeItem.md)**


**[LogCompleteEntry](LogCompleteEntry.md)**


**[LogCreateEntry](LogCreateEntry.md)**



----------------------------------------------------------------------------------------------------------


 





