##### Function : Formula
##### NSFFormulaSummaryItem - Add the item name of a column to a view note's item name list.
---
```
#include <nsfsearc.h>
STATUS LNPUBLIC NSFFormulaSummaryItem(

	FORMULAHANDLE  hFormula,
	const char far *ItemName,
	WORD  ItemNameLength);
```
**Description :**

This function adds the name of a view column to the list of item names
contained in the view's $FORMULA item.

The definition of a view note contains a  $FORMULA item.  This item is of type 
TYPE_FORMULA and contains:

          The view selection formula (compiled using NSFFormulaCompile),
          Any column formulas (also compiled), and 
          A list of the item names of each column in the view.

The  $FORMULA item is constructed as follows:
 
        First, compile the selection formula.
        Then, for each column in the view:
   
         - Compile the column formula.
         - Set the column's itemname in the $FORMULA item by calling
           NSFFormulaSummaryItem().
         - Merge the column formula into the $FORMULA item by calling
           NSFFormulaMerge(). 
 
Please refer to the User Guide for more information about the structure of a 
view note.

**Parameters :**
Input :
hFormula  -  A handle to the formula with which the summary item is to be associated.

ItemName  -  A far pointer to a character string specifying the name of the item to be added to the summary buffer.

ItemNameLength  -  The length of the string specifying the item name.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - STATUS returned from a lower level Notes function called in the action routine and passed back.



**See Also :**
[NSFFormulaCompile](/reference/Func/NSFFormulaCompile)
[NSFFormulaDecompile](/reference/Func/NSFFormulaDecompile)
[NSFFormulaGetSize](/reference/Func/NSFFormulaGetSize)
[NSFFormulaMerge](/reference/Func/NSFFormulaMerge)
---
