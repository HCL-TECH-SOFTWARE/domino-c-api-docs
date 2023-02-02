##### Data Type : Backup
##### LOGRESTORECALLBACKFUNCTION - Definition of the log restore callback function that the backup utility will have to provide for archive logging.
---
##### #include <nsfdb.h>
**Description :**
When Archive logging is in use, this callback function is implemented with the 
following parameters:  

inputs:
LogID - Pointer to the LogID identifying the log series as passed to the 
archive process from NSFGetNextLogToArchive

LogNumber - The log sequence number for the log file as passed to the archive 
process in NSFGetNextLogToArchive.

LogSegmentPathName - A pointer to a null terminated string that specifies the 
full path for where the archived log file should be put.

outputs: 
STATUS - Status of the call: NOERROR if the archive log file is accessible 
through the LogSegmentFullPath.  Any other status indicates an error condition 
and the recovery operation will be stopped.
**See Also :**
[](D:/md_files/.md)
---
