##### Function : Backup
##### NSFGetTransLogStyle - Determine what type of transactional logging is being performed on this server.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFGetTransLogStyle(**

	WORD far *LogType);
**Description :**
This function will determine if transactional logging has been enabled on the 
server and what type of transactional logging is being performed.
**Parameters :**

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - If no other process is currently archiving logs.

ERR_SERVER_NOT_TRANSLOGGED - Transactional logging is not in effect.


LogType  -  When Status returns NOERROR, LogType will be one of the following: TRANSLOG_STYLE_CIRCULAR - for circular logging;  TRANSLOG_STYLE_ARCHIVE - for archive logging

**Sample Usage :**
```
   if ( err = NSFGetTransLogStyle (&LogType))
      print_api_error(err);

      if (LogType == TRANSLOG_STYLE_CIRCULAR)
      {
         printf("\n  Transactional logging is 'CIRCULAR'.\n");
         return 1;
      }

```
**See Also :**
[TRANSLOG_STYLE_xxx](D:/md_files/TRANSLOG_STYLE_xxx.md)
---
