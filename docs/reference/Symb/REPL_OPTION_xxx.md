##### Symbolic Value : Replication
##### REPL_OPTION_xxx - Replication options.
---
```
#include <repl.h>
```

**Symbolic Values :**

	REPL_OPTION_RCV_NOTES	  -  Receive notes from server (pull).

	REPL_OPTION_SEND_NOTES	  -  Send notes to server (push).

	REPL_OPTION_ALL_DBS	  -  Replicate all database (NSF) files, as well as files named in the file list argument.

	REPL_OPTION_CLOSE_SESS	  -  Close sessions when done.

	REPL_OPTION_ALL_NTFS	  -  Replicate all template (NTF) files, as well as files named in the file list argument.

	REPL_OPTION_PRI_LOW	  -  Replicate low, medium, and high priority database.

	REPL_OPTION_PRI_MED	  -  Replicate medium and high priority databases only.

	REPL_OPTION_PRI_HI	  -  Replicate high priority databases only.

	REPL_OPTION_PRIVATE	  -  (For use with ReplicateWithServerExt only) Replicate private documents even if not selected by default.

	REPL_OPTION_ALL_FILES	  -  Replicate all database (NSF) and all template (NTF) files.

	REPL_OPTION_ABSTRACT_RTF	  -  (For use with ReplicateWithServerExt only) Abstract/truncate docs to receive summary and 40KB of rich text only.

	REPL_OPTION_ABSTRACT_SMRY	  -  (For use with ReplicateWithServerExt only) Abstract/truncate docs to summary only data.


**Description :**

These are the options used when calling ReplicateWithServer and ReplicateWithServerExt.  They may be bitwise or'ed together for combined functionality.   Note: these options are now 32-bits.


**See Also :**
[ReplicateWithServer](/domino-c-api-docs/reference/Func/ReplicateWithServer)
[ReplicateWithServerExt](/domino-c-api-docs/reference/Func/ReplicateWithServerExt)
---
