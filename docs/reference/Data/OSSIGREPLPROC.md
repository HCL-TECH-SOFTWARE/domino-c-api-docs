##### Data Type : Signal Handler
##### OSSIGREPLPROC - Function pointer template for replication state signal handler.
---
```
#include <ossignal.h>
```
**Description :**

Definition of a pointer to a function that will handle the replication state 
signal.  

This replication state handler requires three parameters:

   State - Values are defined in REPL_SIGNAL_xxx.

    pText1 - See the following table for detail.

            pText2 - See the following table for detail.
 

State	pText1	pText2
REPL_SIGNAL_IDLE	None	
REPL_SIGNAL_PICKSERVER	None	
REPL_SIGNAL_CONNECTING	pServer	pPort
REPL_SIGNAL_SEARCHING	pServer	pPort
REPL_SIGNAL_SENDING	pServerFile	pLocalFile
REPL_SIGNAL_RECEIVING	pServerFile	pLocalFile
REPL_SIGNAL_SEARCHINGDOCS	pSrcFile	
REPL_SIGNAL_DONEFILE	pLocalFile	pReplFileStats



**See Also :**
[OSSIGPROC](/reference/Data/OSSIGPROC)
[REPL_SIGNAL_xxx](/reference/Symb/REPL_SIGNAL_xxx)
---
