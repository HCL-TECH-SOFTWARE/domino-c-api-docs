##### Symbolic Value : Replication
##### REPL_SIGNAL_xxx - Definitions for replication state signal handler
---
```
#include <ossignal.h>
```

**Symbolic Values :**

	REPL_SIGNAL_IDLE	  -  indicating the connection is done.

	REPL_SIGNAL_PICKSERVER	  -  Display that it is trying to select a server.

	REPL_SIGNAL_CONNECTING	  -  Starting the connection.

	REPL_SIGNAL_SEARCHING	  -  Searching for matching replica on the server.

	REPL_SIGNAL_SENDING	  -  A "push" replication.

	REPL_SIGNAL_RECEIVING	  -  A "pull" replication.

	REPL_SIGNAL_SEARCHINGDOCS	  -  Replicator is in the searching phase.

	REPL_SIGNAL_DONEFILE	  -  Signal the file is done.

	REPL_SIGNAL_REDIRECT	  -  Signal found a redirect.

	REPL_SIGNAL_BUILDVIEW	  -  Signal view is building.


**Description :**




**See Also :**
[OSSIGREPLPROC](/domino-c-api-docs/reference/Data/OSSIGREPLPROC)
---
