##### Function : Progress
##### NEMProgressSetText - set the text for the progress dialog

---
```
#include <progress.h>
#include <addinmen.h>
void LNPUBLIC NEMProgressSetText(HWND progressWindow, char *Text1, char *Text2);
```
**Description:**
set the text for a progress dialog

**Parameters:**

- **progressWindow**
The handle returned from NEMProgressBegin
- **Text1**
The text to display in the progress dialog
- **Text2**
The text to display in the second line of the progress dialog, if the dialog was created with 2 lines of text