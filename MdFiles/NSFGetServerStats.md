




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.0**



**Function : Statistics Reporting**



**NSFGetServerStats** **- Get named
statistics from the server.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetServerStats(**  

      char far \*ServerName,  

      char far \*Facility,  

      char far \*StatName,  

      DHANDLE far \*rethTable,  

      DWORD far \*retTableSize**);**



**Description :**



Request the
specified information from the named server.  Statistics are identified by a
Facility name (see STATPKG\_xxx for Domino facilities) and a Statistic Name.


 


The value of
the statistic is returned in a memory buffer;  the caller is responsible for
freeing this buffer with OSMemFree().  The format of this buffer is the same as
the format of the buffer in the STAT\_RETURN\_BLOCK.  See ParseStats routine in
the Message Queues chapter of the *User Guide* for an example that parses
this buffer.


 


**Parameters :**



Input :  

ServerName  -  Null-terminated string containing the name of the server.  

  

Facility  -  Optional - Null-terminated string containing the name of the
facility.  If no facility name is supplied, pass NULL for this argument.  

  

StatName  -  Optional -  Null-terminated string containing the name of the
desired statistic.  If no statistic name is supplied, pass NULL for this
argument.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

rethTable  -  Handle to the allocated memory block containing the server
statistic.  This memory must be freed by the caller.  

  

retTableSize  -  Size of the returned statistic table, in bytes.  

  




 **See Also :**


**[NSFGetServerLatency](NSFGetServerLatency.md)**


**[STATPKG\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0032008100D8000685256678006EADD9)**


**[StatTraverse](StatTraverse.md)**



----------------------------------------------------------------------------------------------------------


 





