##### Data Type : Note
##### CWF_ERROR_PROC - Pointer to an error callback function called from NSFNoteComputeWithForm().
---
##### #include <nsfnote.h>
**Description :**
If an error is found when validating field values in NSFNoteComputeWithForm(), 
the error callback function is called with information about the problem.  The 
arguments to this callback function are:

   pCDField  - Pointer to the CDField in the form note.

   phase     - Flag indicating the current validation phase.  See CWF_xxx for 
possible values.

   error     - The Domino status code for the error that was detected.

   ErrorText - Handle to memory containing the text that caused the error.  The 
handle is a handle to TYPE_TEXT.  You must get a pointer to the handle by using 
OSLockObject.  Note: Domino or Notes will free the memory for this HANDLE.

   wErrorTextSize - Number of bytes in the error text.

   ctx - 32-bit "CallersContext" value passed to NSFNoteComputeWithForm().

Note:  If the flag CWF_CONTINUE_ON_ERROR is passed in the dwFlags argument of 
NSFNoteComputeWithForm(), error processing for fields will be skipped - the 
callback function will not be invoked.
**See Also :**
[CWF_xxx (Return Codes)](D:/md_files/CWF_xxx (Return Codes).md)
[CWF_xxx (Validation Phases)](D:/md_files/CWF_xxx (Validation Phases).md)
[NSFNoteComputeWithForm](D:/md_files/NSFNoteComputeWithForm.md)
---
