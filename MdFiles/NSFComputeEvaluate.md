




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Function : Formula**



**NSFComputeEvaluate** **- Evaluate
a formula.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**



STATUS
LNPUBLIC **NSFComputeEvaluate(**  

      HCOMPUTE  hCompute,  

      NOTEHANDLE  hNote,  

      DHANDLE far \*rethResult,  

      WORD far \*retResultLength,  

      BOOL far \*retNoteMatchesFormula,  

      BOOL far \*retNoteShouldBeDeleted,  

      BOOL far \*retNoteModified**);**



**Description :**



This
function evaluates a compiled formula with respect to an open note. If an open
note is specified, this obtains variables used in the formula from the open
note and may add or modify fields in the open note.  

  

This function provides several forms of output.  If <rethResult> is
provided, it returns the value resulting from evaluating the formula to the
buffer. (Memory is allocated by this function call for this buffer.  The caller
is responsible for freeing the allocated memory by calling OSMemFree.)  If
<hNote> is provided, it sets new or modified fields in the open note in
memory. If <retNoteMatchesFormula> is provided, it returns a boolean
indicating whether the open note matches the selection portion of the formula.
If <retNoteShouldBeDeleted> is provided, it returns a boolean indicating
whether evaluation of the formula indicates that the open note should be
deleted. If <retNoteModified> is provided, it returns a boolean
indicating whether the open note was modified by evaluating the formula.  

  

NSFComputeEvaluate requires, as input, a "compute handle" which
specifies the formula to evaluate. Before calling NSFComputeEvaluate, call NSFComputeStart,
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


 


 


Note:  A C
API program does not have access to the Domino or Notes context information
that is available when you run a formula through the Notes UI.  Formulas that
use context information may return different results when evaluated in a C API
program.  For example, @IsDocBeingEdited will be evaluated as 0 in a C API
program even if the C API program is editing the note.


 


**Parameters :**



Input :  

hCompute  -  Handle returned by the function NSFComputeStart.  

  

hNote  -  (Optional) Handle to a note to be used as additional variables
available to the formula.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully evaluated the formula for the note.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

rethResult  -  (Optional) A handle to a buffer containing the results of the
formula evaluation.  The buffer starts with a word denoting the datatype,
followed by the data.  The datatype will usually be one of the list versions of
the simple datatypes (TYPE\_TEXT\_LIST, TYPE\_TIME\_RANGE, or TYPE\_NUMBER\_RANGE),
but the application should be prepared to handle the simple datatypes as well.  

  

Memory space for this buffer is allocated with OSMemAlloc.  The caller is
responsible for freeing the memory by calling OSMemFree.  

  

retResultLength  -  (Optional) The length of the result buffer.  

  

retNoteMatchesFormula  -  (Optional) TRUE if note "matches" SELECT
portion of formula.  

  

retNoteShouldBeDeleted  -  (Optional) TRUE if formula indicates that note
should be deleted (result is @UNAVAILABLE).  

  

retNoteModified  -  (Optional) TRUE if the note was modified by the formula.  

  




 **Sample Usage :**


   

/\*  

 \* Evaluate the formula just compiled against the note just opened.  

 \*/  

   

    if (sError = NSFComputeEvaluate(hCompute,  

                                    hNote,  

                                    (DHANDLE far \*) &hResult,  

                                    &wResultLen,  

                                    0,  

                                    0,  

                                    0))  

        return (ERR(sError));  

  

    <make use of the result>  

  

    OSMemFree (hResult);  

  




 **See Also :**


**[NSFComputeStart](NSFComputeStart.md)**


**[NSFComputeStop](NSFComputeStop.md)**


**[NSFFormulaCompile](NSFFormulaCompile.md)**


**[OSMemFree](OSMemFree.md)**



----------------------------------------------------------------------------------------------------------


 





