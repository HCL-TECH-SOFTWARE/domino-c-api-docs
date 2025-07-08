##### Function : Progress
##### NEMProgressSetBarRange

---
```
#include <progress.h>
#include <addinmen.h>
void LNPUBLIC NEMProgressSetBarRange(HWND progressWindow, DWORD range);
```
**Description :**

Sets the progress range for a specific operation.

This API allows you to define the maximum values for a progress indicator, which is typically used to visually represent the completion status of a long-running task.  The minimum value is always zero.

**Parameters :**

- **progressWindow**  

    The handle returned from NEMProgressBegin.

- **range**  

    The maximum value for the progress.

**Remarks :**

Call this method before updating the progress value to ensure the progress bar or indicator reflects the correct range for the current operation.

