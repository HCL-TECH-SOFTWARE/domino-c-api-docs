##### Data Type : Mail Gateway
##### MAIL_ROUTING_ACTIONS - Type of mail connection for next hop.
---
```
#include <mailserv.h>
```

**Definition :**

typedef enum {
   MAIL_ERROR,
   MAIL_TRANSFER,
   MAIL_DELIVER,
   MAIL_FORWARD
} MAIL_ROUTING_ACTIONS;

**Description :**

Values from this enumeration type are returned by MailFindNextHopToRecipient() to indicate the type of mail connection.  The connection types are:
<ul>
<ul><br>
MAIL_ERROR -- No further routing information could be found.<br>
<br>
MAIL_TRANSFER -- The connection is to another mail server.<br>
<br>
MAIL_DELIVER -- This server is the recipient's mail server.<br>
<br>
MAIL_FORWARD -- Recipient has a forwarding address.</ul>
</ul>



**See Also :**
[MailFindNextHopToRecipient](/domino-c-api-docs/reference/Func/MailFindNextHopToRecipient)
---
