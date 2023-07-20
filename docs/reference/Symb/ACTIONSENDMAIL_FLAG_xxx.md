##### Symbolic Value : Agents
##### ACTIONSENDMAIL_FLAG_xxx - Option flags for CDACTIONSENDMAIL record.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ACTIONSENDMAIL_FLAG_INCLUDEDOC	  -  Include original document in message.

	ACTIONSENDMAIL_FLAG_INCLUDELINK	  -  Include doclink to document.

	ACTIONSENDMAIL_FLAG_SAVEMAIL	  -  Save a copy of the message.

	ACTIONSENDMAIL_FLAG_TOFORMULA	  -  "To" field is a formula.

	ACTIONSENDMAIL_FLAG_CCFORMULA	  -  "cc" field is a formula.

	ACTIONSENDMAIL_FLAG_BCCFORMULA	  -  "bcc" field is a formula.

	ACTIONSENDMAIL_FLAG_SUBJECTFORMULA	  -  "Subject" field is a formula.


**Description :**

These flags specify options for the Send Mail action for a Agent.  These flags are stored in the dwFlags field of the CDACTIONSENDMAIL structure.


**See Also :**
[CDACTIONNEWSLETTER](/domino-c-api-docs/reference/Data/CDACTIONNEWSLETTER)
[CDACTIONSENDMAIL](/domino-c-api-docs/reference/Data/CDACTIONSENDMAIL)
---
