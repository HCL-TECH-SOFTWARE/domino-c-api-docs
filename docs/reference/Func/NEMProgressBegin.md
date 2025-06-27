##### Function : Progress
##### NEMProgressBegin - show a progress dialog

---
```
#include <progress.h>
HWND LNPUBLIC NEMProgressBegin(WORD Flags);
```
**Description:**
Begin showing a progress dialog.

**Parameters:**

- **Flags**  
    - `0`: Indicates a single line of text  
    - `1`: Indicates two lines of text  

**Returns:**

- `0`: An error occurred  
- Any other value: The window handle to use for future calls  

**Sample Usage:**
```
HWND progressWindow = NEMProgressBegin(0);
if (0 == progressWindow) {
    // ERROR
    return;
}
NEMProgressSetText(progressWindow, "Doing work...", NULL);
NEProgressSetBarRange(progressWindow, 100);

// update position over time
NEMProgressSetBarPos(progressWindow, position);

// When the work as completed:
NEMProgressEnd(progressWindow);
```