##### Data Type : Note
##### CWF_ERROR_PROC - Pointer to an error callback function called from NSFNoteComputeWithForm().
---
```
#include <nsfnote.h>
```

**Definition :**

typedef WORD (LNCALLBACKPTR CWF_ERROR_PROC)(
   const void far *pCDField,
   WORD phase,
   STATUS error,
   HANDLE ErrorText,
   WORD wErrorTextSize,
   void far *ctx);

**Description :**

If an error is found when validating field values in NSFNoteComputeWithForm(), the error callback function is called with information about the problem.  The arguments to this callback function are:
<ul><br>
<br>
   pCDField  - Pointer to the CDField in the form note.<br>
<br>
   phase     - Flag indicating the current validation phase.  See CWF_xxx for possible values.<br>
<br>
   error     - The Domino status code for the error that was detected.<br>
<br>
   ErrorText - Handle to memory containing the text that caused the error.  The handle is a handle to TYPE_TEXT.  You must get a pointer to the handle by using OSLockObject.  Note: Domino or Notes will free the memory for this HANDLE.<br>
<br>
   wErrorTextSize - Number of bytes in the error text.<br>
<br>
   ctx - 32-bit &quot;CallersContext&quot; value passed to NSFNoteComputeWithForm().<br>
<br>
<b>Note:</b>  If the flag CWF_CONTINUE_ON_ERROR is passed in the dwFlags argument of NSFNoteComputeWithForm(), error processing for fields will be skipped - the callback function will not be invoked.</ul>



**See Also :**
[CWF_xxx (Return Codes)](/domino-c-api-docs/reference/Symb/CWF_xxx (Return Codes))
[CWF_xxx (Validation Phases)](/domino-c-api-docs/reference/Symb/CWF_xxx (Validation Phases))
[NSFNoteComputeWithForm](/domino-c-api-docs/reference/Func/NSFNoteComputeWithForm)
---
