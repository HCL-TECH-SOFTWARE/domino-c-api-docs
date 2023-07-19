##### Data Type : Signal Handler
##### OSSIGREPLPROC - Function pointer template for replication state signal handler.
---
```
#include <ossignal.h>
```

**Definition :**

typedef void (LNCALLBACKPTR OSSIGREPLPROC)(
   WORD State,
   char far *pText1,
   char far *pText2);

**Description :**

Definition of a pointer to a function that will handle the replication state signal.  <br>
<br>
This replication state handler requires three parameters:<br>
<br>
   <b>State </b>- Values are defined in REPL_SIGNAL_xxx.<br>
<br>
    <b>pText1 </b>- See the following table for detail.<br>
<br>
            <b>pText2 </b>- See the following table for detail.<br>
 <br>

<table width="100%" border="1">
<tr valign="top"><td width="33%">State</td><td width="33%">pText1</td><td width="33%">pText2</td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_IDLE</b></td><td width="33%">None</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_PICKSERVER</b></td><td width="33%">None</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_CONNECTING</b></td><td width="33%">pServer</td><td width="33%">pPort</td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_SEARCHING</b></td><td width="33%">pServer</td><td width="33%">pPort</td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_SENDING</b></td><td width="33%">pServerFile</td><td width="33%">pLocalFile</td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_RECEIVING</b></td><td width="33%">pServerFile</td><td width="33%">pLocalFile</td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_SEARCHINGDOCS</b></td><td width="33%">pSrcFile</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><b>REPL_SIGNAL_DONEFILE</b></td><td width="33%">pLocalFile</td><td width="33%">pReplFileStats</td></tr>
</table>



**See Also :**
[OSSIGPROC](/domino-c-api-docs/reference/Data/OSSIGPROC)
[REPL_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/REPL_SIGNAL_xxx)
---
