##### Function : Progress
##### NEMProgressDeltaPos - increment the progress

---
```
#include <progress.h>
#include <addinmen.h>
STATUS LNPUBLIC NEMProgressDeltaPos(HWND progressWindow, DWORD delta);
```
**Description :**

Increment the progress

**Parameters :**

- **progressWindow**
The handle returned from NEMProgressBegin

- **delta**
The amount to add to the current progress.

**Returns :**

- ERR_CANCEL - The user requested to cancel
- NOERROR - continue
