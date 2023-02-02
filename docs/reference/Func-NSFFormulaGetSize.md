##### Function : Formula
##### NSFFormulaGetSize - Computes the length of a compiled formula.
---
##### #include <nsfsearc.h>
STATUS LNPUBLIC **NSFFormulaGetSize(**

	FORMULAHANDLE  hFormula,
	WORD far *retFormulaLength);
**Description :**
This function accepts a handle to a compiled formula and returns its length in 
bytes.
**Parameters :**
Input :
hFormula  -  A handle of a compiled formula.

retFormulaLength  -  Address of an int variable in which to store the formula length.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - STATUS returned from a lower level Notes function called in the action routine and passed back.


**Sample Usage :**
```
 
```
**See Also :**
[NSFFormulaMerge](D:/md_files/NSFFormulaMerge.md)
---
