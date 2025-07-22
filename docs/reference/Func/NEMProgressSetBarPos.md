##### Function : Progress
##### NEMProgressSetBarPos

---
```
#include <progress.h>
#include <addinmen.h>
STATUS LNPUBLIC NEMProgressSetBarPos(HWND progressWindow, DWORD position);
```
**Description :**

Set the current position of the progress

**Parameters:**

- **progressWindow**
The handle returned from NEMProgressBegin

- **position**
The current position of the progress. Must be less than the value set for NEMProgressSetBarRange

**Returns :**
- ERR_CANCEL - The user requested to cancel
- NOERROR - continue
