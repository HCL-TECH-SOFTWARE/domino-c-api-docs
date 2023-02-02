##### Function : Formula
##### NSFComputeStart - Perform some initialization prior to formula evaluation.
---
##### #include <nsfsearc.h>
STATUS LNPUBLIC **NSFComputeStart(**

	WORD  Flags,
	void far *lpCompiledFormula,
	HCOMPUTE far *rethCompute);
**Description :**
This function takes a pointer to a compiled formula as input and returns an 
HCOMPUTE variable as output.  The HCOMPUTE variable is used by Domino and Notes 
to uniquely identify the formula being evaluated.  This function MUST be called 
before calling NSFComputeEvaluate.
**Parameters :**
Input :
Flags  -  Reserved - must be set to 0;

lpCompiledFormula  -  A far void pointer to a compiled formula (A formula is compiled by calling NSFFormulaCompile).  On UNIX systems, this parameter must be word-aligned.

Output :
(routine)  -  
NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethCompute  -  A far pointer to an HCOMPUTE variable.  The HCOMPUTE variable is passed as input to the function NSFComputeEvaluate to identify the formula to be evaluated.

**See Also :**
[NSFComputeEvaluate](D:/md_files/NSFComputeEvaluate.md)
[NSFComputeStop](D:/md_files/NSFComputeStop.md)
---
