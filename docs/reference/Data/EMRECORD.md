##### Data Type : Extension Manager
##### EMRECORD - Data structure passed to EMHANDLER callback functions.
---
```
#include <extmgr.h>
```
**Description :**

This structure contains context information provided by the extension manager 
facility.  Information in the structure identifies the operation being 
performed and provides access to the arguments of the Domino or Notes core 
function.

The fields in this structure are:

EId - Extension manager ID code for the core function call;  see EM_xxx for a 
list of function codes.

NotificationType - This field will be set to EM_BEFORE if the callback function 
is being called before the operation is attempted, or EM_AFTER if the callback 
function is being called after the operation is completed.

Status - If the NotificationType is EM_AFTER, this field contains the status 
value from the core operation.

Ap - Pointer to the argument list provided to the core function.  The format of 
the argument list depends on the actual function.  These parameters may be 
accessed using the variable argument macros;  see VARARG_PTR for more 
information.

**See Also :**
[EID](/domino-c-api-docs/reference/Data/EID)
[EMHANDLER](/domino-c-api-docs/reference/Data/EMHANDLER)
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
[VARARG_PTR](/domino-c-api-docs/reference/Data/VARARG_PTR)
---
