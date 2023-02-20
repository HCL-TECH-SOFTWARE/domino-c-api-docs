##### Data Type : Remote LAN adapter
##### PREMOTE_LAN_STATUS_CALLBACK - Calling convention for remote LAN service product adapter callback function.
---
```
#include <net.h>
```
**Description :**

This typedef defines the interface to a status callback routine for a remote 
LAN service product adapter.  Notes hands the address of this routine to the 
initialization function of the LAN service product.  The LAN service product 
calls this routine to report ongoing status back to Notes and for Notes to 
display this status information.  It also checks for a user abort condition 
(e.g.  ctl+break for a PC, or command-period for a Macintosh).

Inputs:
  Action The type of operation needed. See REMOTE_LAN_xxx for possible values.

	StatusCode A Remote LAN status code, if  type is  
REMOTE_LAN_DISPLAY_STATUS.  See REMOTE_LANT_STATUS_xxx for possible codes.

	pErrText         The error string, if  type is  
REMOTE_LAN_DISPLAY_ERROR_TEXT.

Outputs:
(routine) The return argument is of type BOOL.  This is used to return an abort 
condition if one has occurred.  It should be TRUE (1) if operation should 
continue, and FALSE (0) if the user has asked for an abort (e.g. ctl+break for 
a PC, or command-period for a Macintosh).

**See Also :**
[PREMOTE_LAN_SERVICE_ENTRY](/reference/Data/PREMOTE_LAN_SERVICE_ENTRY)
[REMOTE_LAN_STATUS_xxx](/reference/Symb/REMOTE_LAN_STATUS_xxx)
---
