##### Function : Note
##### NSFNoteComputeWithForm - Validate the note against the form.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteComputeWithForm(**

	NOTEHANDLE  hNote,
	NOTEHANDLE  hFormNote,
	DWORD  dwFlags,
	CWF_ERROR_PROC  ErrorRoutine,
	void *CallersContext);
**Description :**
Given a handle to an open note and a handle to an open form note, for each 
field defined in the form, this function will:

1)  Validate fields with Default Value formulas,

2)  Validate fields with Translation formulas,

3)  Validate fields with Validation formulas,

4)  Calculate values for Computed fields.

If no error callback routine is supplied and the flag CWF_CONTINUE_ON_ERROR is 
not set (in the dwFlags argument), if one of the validation formulas fails, an 
error is returned.  If the CWF_CONTINUE_ON_ERROR flag is set, the error is not 
returned.

If a pointer to an error callback routine is supplied and one of the validation 
formulas fails, the error callback routine is called.  The argument 
CallersContext is passed directly to the error callback.  For the calling 
sequence and arguments, see the data type CWF_ERROR_PROC.  If the 
CWF_CONTINUE_ON_ERROR flag is set, error processing for the field is skipped;  
if a pointer to a callback function is supplied, the callback function will be 
ignored.
**Parameters :**
Input :
hNote  -  Handle to the note to be validated.

hFormNote  -  Handle to the form note.   If NULLHANDLE is specified, then the function will use the note's embedded form; if there is no embedded form, it will use the form specified in the form field; if there is no form field, this function will use the default database form.

dwFlags  -  Validation flags.  For the values supported, see the symbolic value CWF_xxx.

ErrorRoutine  -  Pointer to the error callback routine.

CallersContext  -  Context information to pass to the error callback routine.  This 32-bit value is passed unchanged to the callback.

Output :
(routine)  -  Return status from this call:

NOERROR - Success

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**Sample Usage :**
```
...

/* Create a note and add all input data to it. */
    if (error = NSFNoteCreate (db_handle, &note_handle))
    {
        NSFDbClose (db_handle);
        API_RETURN (ERR(error));
    }

/* Prompt for input data. */
    PromptValues(&length, &width);

/* Set the input data measurement */
    temp_val = (NUMBER) length;
    if (error = NSFItemSetNumber (note_handle, "Length", &temp_val))
        goto Item_Error;

    temp_val = (NUMBER) width;
    if (error = NSFItemSetNumber (note_handle, "Width", &temp_val))
        goto Item_Error;

/* Call NSFNoteComputeWithForm to 
 * 1) ensure that input measurement data is valid, or flag error in callback
 * 2) compute the output measurement data, or flag error in callback
 */
    if (error = NSFNoteComputeWithForm (note_handle, NULLHANDLE, (DWORD) 0,
                                        CWFCallback, NULL))
        goto Item_Error;

/* No error; get entered and computed field values and display measurement 
summary */
    if (NSFItemGetNumber (note_handle, "Length", &length) == FALSE)
        goto Item_Error;
    if (NSFItemGetNumber (note_handle, "Width", &width) == FALSE)
        goto Item_Error;
    if (NSFItemGetNumber (note_handle, "Perimeter", &perimeter) == FALSE)
        goto Item_Error;
    if (NSFItemGetNumber (note_handle, "Area", &area) == FALSE)
        goto Item_Error;
    DisplayValues(length, width, perimeter, area);

/* Update the note. */
    if (error = NSFNoteUpdate (note_handle, 0))
        goto Item_Error;

...
```
**See Also :**
[CWF_ERROR_PROC](D:/md_files/CWF_ERROR_PROC.md)
[CWF_xxx (Return Codes)](D:/md_files/CWF_xxx (Return Codes).md)
[CWF_xxx (Validation Phases)](D:/md_files/CWF_xxx (Validation Phases).md)
---
