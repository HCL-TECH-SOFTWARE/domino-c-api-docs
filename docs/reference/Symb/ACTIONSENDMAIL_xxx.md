##### Symbolic Value : Agents
##### ACTIONSENDMAIL_xxx - CDACTIONSENDMAIL record field array indexes
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ACTIONSENDMAIL_FIELDCOUNT	  -  Number of elements in the SendMail action field size array.

	ACTIONSENDMAIL_TOFIELD	  -  Index of the "To" field length.

	ACTIONSENDMAIL_CCFIELD	  -  Index of the "Cc" field length.

	ACTIONSENDMAIL_BCCFIELD	  -  Index of the "Bcc" field length.

	ACTIONSENDMAIL_SUBJECTFIELD	  -  Index of the "Subject" field length.

	ACTIONSENDMAIL_BODYFIELD	  -  Index of the "Body" field length.


**Description :**

The CDACTIONSENDMAIL record contains an array of length values for the SendMail action fields.  These values are used to index into the array.


**See Also :**
[CDACTIONNEWSLETTER](/domino-c-api-docs/reference/Data/CDACTIONNEWSLETTER)
[CDACTIONSENDMAIL](/domino-c-api-docs/reference/Data/CDACTIONSENDMAIL)
---
