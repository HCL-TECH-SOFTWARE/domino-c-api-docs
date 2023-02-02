##### Function : Formula
##### NSFComputeStop - Terminate evaluation of a formula.
---
##### #include <nsfsearc.h>
STATUS LNPUBLIC **NSFComputeStop(**

	HCOMPUTE  hCompute);
**Description :**
This function is called to terminate the evaluation of a formula. 
**Parameters :**
Input :
hCompute  -  The HCOMPUTE variable that was returned by the corresponding call to NSFComputeStart.

Output :
(routine)  -  
NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


**See Also :**
[NSFComputeStart](D:/md_files/NSFComputeStart.md)
[NSFComputeEvaluate](D:/md_files/NSFComputeEvaluate.md)
---
