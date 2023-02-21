##### Function : Formula
##### NSFFormulaCompile - Compiles a formula into binary form.
---
```
#include <nsfsearc.h>
STATUS LNPUBLIC NSFFormulaCompile(

	char far *FormulaName,
	WORD  FormulaNameLength,
	const char far *FormulaText,
	WORD  FormulaTextLength,
	FORMULAHANDLE far *rethFormula,
	WORD far *retFormulaLength,
	STATUS far *retCompileError,
	WORD far *retCompileErrorLine,
	WORD far *retCompileErrorColumn,
	WORD far *retCompileErrorOffset,
	WORD far *retCompileErrorLength);
```
**Description :**

This function accepts a LMBCS string containing a formula and translates the 
formula into binary form.  Functions that take compiled formulas as parameters 
include NSFSearch and NSFComputeStart.

After you use the compiled formula (returned in argument 5) you must deallocate 
the buffer that holds the formula.  Do this by calling OSMemFree and passing it 
the FORMULAHANDLE.

**Parameters :**
Input :
FormulaName  -  A pointer to a name for this formula. Specify NULL for this parameter unless the formula is going to be a column formula in a view note;  in this case, specify the column's item name for this parameter.  

FormulaNameLength  -  The length of formula's name.  If the previous parameter is NULL, set this parameter to 0. 

FormulaText  -  A pointer to the LMBCS text of the formula.

FormulaTextLength  -  The length of the formula text.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.  The return codes include:

NOERROR
ERR_FORMULA_COMPILATION

If you receive the second return code, more information about the error is available in arguments 7 through 11 of the call.


rethFormula  -  A pointer to a FORMULAHANDLE that will receive the handle of the compiled formula

retFormulaLength  -  A pointer to a WORD that will receive the length of the compiled formula.

retCompileError  -  A pointer to a STATUS that will receive any compilation error (from translating the character text formula to binary).

retCompileErrorLine  -  A pointer to a WORD that will receive the line number of any compilation error.  This information is used by the Notes screen interface.

retCompileErrorColumn  -  A pointer to a WORD that will receive the column number of any compilation error.  This information is used by the Notes screen interface.

retCompileErrorOffset  -  A pointer to a WORD that will receive the offset (within the formula) of any compilation error.  You may use this information within your program to find the error.

retCompileErrorLength  -  A pointer to a WORD that will receive the length of any compilation error.  You may use this information (with retCompileErrorOffset) to find the error.


**Sample Usage :**
```

sError = NSFFormulaCompile( NULL,
                            0,
                            szSelFormula,
                            strlen(szSelFormula),
                            &hSelFormula,
                            &wSelFormulaLen,
                            &wdc, &wdc, &wdc,
                            &wdc, &wdc );
```
**See Also :**
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
[NSFComputeStart](/domino-c-api-docs/reference/Func/NSFComputeStart)
[NSFComputeEvaluate](/domino-c-api-docs/reference/Func/NSFComputeEvaluate)
---
