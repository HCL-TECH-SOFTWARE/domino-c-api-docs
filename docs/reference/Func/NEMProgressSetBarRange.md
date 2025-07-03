##### Function : Progress
##### NEMProgressSetBarRange

---
```
#include <progress.h>
#include <addinmen.h>
void LNPUBLIC NEMProgressSetBarRange(HWND progressWindow, DWORD range);
```
**Description:**
Set the range of the progress

**Parameters:**

- **progressWindow**
The handle returned from NEMProgressBegin

- **range**
The maximum value for the progress