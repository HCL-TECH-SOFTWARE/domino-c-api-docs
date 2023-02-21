##### Data Type : Agents
##### CDACTIONSENDMAIL - Send Mail action CD record.
---
```
#include <queryods.h>
```
**Description :**

The Send Mail action is stored in a CDACTIONSENDMAIL record in fields of type 
TYPE_ACTION, usually the action field of an Agent.  The fields in this 
structure are:

Header     SIG_ACTION_SENDMAIL and total record length
dwFlags    ACTIONSENDMAIL_FLAG_xxx flags
wFieldLen  Array of lengths for the send mail fields

This record is followed by the string values for the send mail fields.  These 
strings are not in packed format;  each string has a NUL terminator, and may 
contain a padding byte if necessary to make the length an even number of 
bytes.  The strings contain:

To  Recipient list
Cc  Courtesy copy recipient list
Bcc  "Blind" courtesy copy recipient list
Subject  Message subject
Body  Message body


**See Also :**
[ACTIONSENDMAIL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIONSENDMAIL_FLAG_xxx)
[ACTIONSENDMAIL_xxx](/domino-c-api-docs/reference/Symb/ACTIONSENDMAIL_xxx)
---
