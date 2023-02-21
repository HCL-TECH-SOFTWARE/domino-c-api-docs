##### Data Type : Mail Gateway
##### MAIL_ROUTING_ACTIONS - Type of mail connection for next hop.
---
```
#include <mailserv.h>
```
**Description :**

Values from this enumeration type are returned by MailFindNextHopToRecipient() 
to indicate the type of mail connection.  The connection types are:

MAIL_ERROR -- No further routing information could be found.

MAIL_TRANSFER -- The connection is to another mail server.

MAIL_DELIVER -- This server is the recipient's mail server.

MAIL_FORWARD -- Recipient has a forwarding address.

**See Also :**
[MailFindNextHopToRecipient](/domino-c-api-docs/reference/Func/MailFindNextHopToRecipient)
---
