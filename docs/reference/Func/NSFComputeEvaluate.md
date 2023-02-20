##### Function : Formula
##### NSFComputeEvaluate - Evaluate a formula.
---
```
#include <nsfsearc.h>
STATUS LNPUBLIC NSFComputeEvaluate(

	HCOMPUTE  hCompute,
	NOTEHANDLE  hNote,
	DHANDLE far *rethResult,
	WORD far *retResultLength,
	BOOL far *retNoteMatchesFormula,
	BOOL far *retNoteShouldBeDeleted,
	BOOL far *retNoteModified);
```
**Description :**

This function evaluates a compiled formula with respect to an open note. If an 
open note is specified, this obtains variables used in the formula from the 
open note and may add or modify fields in the open note.

This function provides several forms of output.  If <rethResult> is provided, 
it returns the value resulting from evaluating the formula to the buffer. 
(Memory is allocated by this function call for this buffer.  The caller is 
responsible for freeing the allocated memory by calling OSMemFree.)  If <hNote> 
is provided, it sets new or modified fields in the open note in memory. If 
<retNoteMatchesFormula> is provided, it returns a boolean indicating whether 
the open note matches the selection portion of the formula. If 
<retNoteShouldBeDeleted> is provided, it returns a boolean indicating whether 
evaluation of the formula indicates that the open note should be deleted. If 
<retNoteModified> is provided, it returns a boolean indicating whether the open 
note was modified by evaluating the formula.

NSFComputeEvaluate requires, as input, a "compute handle" which specifies the 
formula to evaluate. Before calling NSFComputeEvaluate, call NSFComputeStart, 
specifying a compiled Domino formula, to obtain this compute handle. A single 
compute handle will suffice to evaluate a single formula with respect to many 
different notes.  Thus, you may call NSFComputeStart once, then call 
NSFComputeEvaluate many times.

Note: NSFComputeEvaluate may execute any formula that does not include one of 
the following functions. These functions depend on Notes user interface 
functionality. Any formula that uses one of these functions will have no effect 
when evaluated from an API program using NSFComputeEvaluate:

     @Command
    @DbLookup
    @DbColumn
    @DDEInitiate
    @DDETerminate
    @DDEExecute
    @DDEPoke
    @MailSend


Note:  A C API program does not have access to the Domino or Notes context 
information that is available when you run a formula through the Notes UI.  
Formulas that use context information may return different results when 
evaluated in a C API program.  For example, @IsDocBeingEdited will be evaluated 
as 0 in a C API program even if the C API program is editing the note.

**Parameters :**
Input :
hCompute  -  Handle returned by the function NSFComputeStart.

hNote  -  (Optional) Handle to a note to be used as additional variables available to the formula.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully evaluated the formula for the note.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


rethResult  -  (Optional) A handle to a buffer containing the results of the formula evaluation.  The buffer starts with a word denoting the datatype, followed by the data.  The datatype will usually be one of the list versions of the simple datatypes (TYPE_TEXT_LIST, TYPE_TIME_RANGE, or TYPE_NUMBER_RANGE), but the application should be prepared to handle the simple datatypes as well.

Memory space for this buffer is allocated with OSMemAlloc.  The caller is responsible for freeing the memory by calling OSMemFree.

retResultLength  -  (Optional) The length of the result buffer.

retNoteMatchesFormula  -  (Optional) TRUE if note "matches" SELECT portion of formula.

retNoteShouldBeDeleted  -  (Optional) TRUE if formula indicates that note should be deleted (result is @UNAVAILABLE).

retNoteModified  -  (Optional) TRUE if the note was modified by the formula.


**Sample Usage :**
```
 
/*
 * Evaluate the formula just compiled against the note just opened.
 */
 
    if (sError = NSFComputeEvaluate(hCompute,
                                    hNote,
                                    (DHANDLE far *) &hResult,
                                    &wResultLen,
                                    0,
                                    0,
                                    0))
        return (ERR(sError));

    <make use of the result>

    OSMemFree (hResult);

```
**See Also :**
[NSFComputeStart](/reference/Func/NSFComputeStart)
[NSFComputeStop](/reference/Func/NSFComputeStop)
[NSFFormulaCompile](/reference/Func/NSFFormulaCompile)
[OSMemFree](/reference/Func/OSMemFree)
---
