




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Replication**



**REPL\_OPTION\_xxx** **-** Replication
options.


**----------------------------------------------------------------------------------------------------------**



**#include <repl.h>**


 **Symbolic Values :**      REPL\_OPTION\_RCV\_NOTES          -  Receive notes from server
(pull).  

  

      REPL\_OPTION\_SEND\_NOTES        -  Send notes to server (push).  

  

      REPL\_OPTION\_ALL\_DBS    -  Replicate all database (NSF) files, as well as
files named in the file list argument.  

  

      REPL\_OPTION\_CLOSE\_SESS         -  Close sessions when done.  

  

      REPL\_OPTION\_ALL\_NTFS   -  Replicate all template (NTF) files, as well as
files named in the file list argument.  

  

      REPL\_OPTION\_PRI\_LOW    -  Replicate low, medium, and high priority
database.  

  

      REPL\_OPTION\_PRI\_MED    -  Replicate medium and high priority databases
only.  

  

      REPL\_OPTION\_PRI\_HI        -  Replicate high priority databases only.  

  

      REPL\_OPTION\_PRIVATE    -  (For use with ReplicateWithServerExt only)
Replicate private documents even if not selected by default.  

  

      REPL\_OPTION\_ALL\_FILES              -  Replicate all database (NSF) and
all template (NTF) files.  

  

      REPL\_OPTION\_ABSTRACT\_RTF    -  (For use with ReplicateWithServerExt only)
Abstract/truncate docs to receive summary and 40KB of rich text only.  

  

      REPL\_OPTION\_ABSTRACT\_SMRY             -  (For use with
ReplicateWithServerExt only) Abstract/truncate docs to summary only data.  

  




**Description :**



These are
the options used when calling ReplicateWithServer and ReplicateWithServerExt. 
They may be bitwise or'ed together for combined functionality.   Note: these
options are now 32-bits.


 **See Also :**


**[ReplicateWithServer](ReplicateWithServer.md)**


**[ReplicateWithServerExt](ReplicateWithServerExt.md)**



----------------------------------------------------------------------------------------------------------


 





