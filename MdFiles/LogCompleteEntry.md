




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



**LogCompleteEntry** **- Allow
writing the log entry to disk.**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNPUBLIC **LogCompleteEntry(**  

      WORD  LogEntry**);**



**Description :**



Given the
number of a log entry, this function adds an item called FinishTime to the
entry and marks the entry "complete", "modified", and
"not locked", allowing the entry to be written to disk and
deallocated.  Log entries are written to disk at set intervals or when a client
or server component attempts to read from the log (to ensure that the request
obtains the most up-to-date information).  In addition, if any log messages
have not been written to disk when the API program terminates, these messages
are written at that time.


 


**Parameters :**



Input :  

LogEntry  -  A WORD containing the number of the log entry you would like to
write to the Log database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully completed the log entry.  

  

ERR\_LOG\_NULLHANDLE - Log Entry not allocated.  The Log Package is no longer
available.  

  

ERR\_LOGENTRY\_INVALID - LogEntry out of range.  

  

ERR\_LOG\_RESERVED\_ENTRY - LogEntry reserved.  Meaning that the log entry number
supplied is less than or equal to MAX\_RESERVED\_LOG\_ENTRY.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and display
the error for the user.  

  

  




 **Sample Usage :**


/\* Automatically fill
FinishTime item/field  and recycle the log \*/  

/\* entry(unlocks the object)                                     \*/  

  

if (error\_status = LogCompleteEntry(log\_entry))  

   goto Exit;  

else  

   cleanup\_state -= COMPLETE\_LOG\_ENTRY;


 **See Also :**


**[LogCloseEntry](LogCloseEntry.md)**


**[LogCreateEntry](LogCreateEntry.md)**



----------------------------------------------------------------------------------------------------------


 





