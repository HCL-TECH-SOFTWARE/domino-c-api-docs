##### Function : Formula
##### NSFFormulaMerge - Combines two compiled formulas into a single compiled formula.
---
```
#include <nsfsearc.h>
STATUS LNPUBLIC NSFFormulaMerge(

	FORMULAHANDLE  hSrcFormula,
	FORMULAHANDLE  hDestFormula);
```
**Description :**

This function accepts handles to two compiled formulas merges them into a 
single compiled formula.      NSFFormulaMerge is designed to facilitate 
constructing the $FORMULA item of a view note, which contains formulas for the 
view and for all of the columns.

Note that if you use NSFFormulaMerge with two compiled formulas with main 
expressions, hDestForumula will be overwritten by hSrcFormula.

**Parameters :**
Input :
hSrcFormula  -  A handle to a compiled formula which is to be merged into the other formula.

hDestFormula  -  A handle to a compiled formula.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - STATUS returned from a lower level Notes function called in the action routine and passed back.


hDestFormula  -  A handle to the merged formula.


**Sample Usage :**
```
/* 
 * this code fragment illustrates using NSFFormulaMerge to
 * help construct the $FORMULA item of a view note 
 */
... 
/*
 * Compile and set the selection formula to show all notes.
 */

    sError = NSFFormulaCompile( NULL,
                                0,
                                szSelFormula,
                                (WORD) strlen(szSelFormula),
                                &hSelFormula,
                                &wSelFormulaLen,
                                &wdc, &wdc, &wdc,
                                &wdc, &wdc );

    if (sError)
    {
        printf("Error: unable to compile selection formula '%s'.\n", 
                szSelFormula );
        goto Exit;
    }    

/*
 * Compile the formula for column 1.
 */
     
    sError = NSFFormulaCompile( szItemName_1,
                                wItemName_1_Len,
                                szFormula_1,
                                (WORD) strlen(szFormula_1),
                                &hFormula_1,
                                &wFormula_1_Len,
                                &wdc, &wdc, &wdc,
                                &wdc, &wdc );

    if (sError)
    {
        printf("Error: unable to compile column 1 formula '%s'.\n", 
                szFormula_1 );
        goto Exit;
    }    


/*
 * Set summary item by merging column 1 formula into selection formula.
 */

    sError = NSFFormulaSummaryItem( hSelFormula,
                    szItemName_1,
                    wItemName_1_Len );
    if (sError)
    {
        printf("Error: unable to set summary item '%s'.\n", 
                szItemName_1 );
        goto Exit;
    }    
    
    
    sError = NSFFormulaMerge( hFormula_1, hSelFormula );
    if (sError)
    {
        printf("Error: unable to merge column 1 formula into selection 
formula.\n");
        goto Exit;
    }
    

/*
 * Compile the formula for column 2.
 */
     
    sError = NSFFormulaCompile( szItemName_2,
                                wItemName_2_Len,
                                szFormula_2,
                                (WORD) strlen(szFormula_2),
                                &hFormula_2,
                                &wFormula_2_Len,
                                &wdc, &wdc, &wdc,
                                &wdc, &wdc );
    if (sError)
    {
        printf("Error: unable to compile column 2 formula '%s'.\n", 
                szFormula_2 );
        goto Exit;
    }    


/*
 * Set this item as a summary item by merging the column 2
 * formula into the selection formula.
 */

    sError = NSFFormulaSummaryItem( hSelFormula,
                                    szItemName_2,
                                    wItemName_2_Len );
    if (sError)
    {
        printf("Error: unable to merge column 2 item name into selection 
formula.\n");
        goto Exit;
    }    

    sError = NSFFormulaMerge( hFormula_2, hSelFormula );
    if (sError)
    {
        printf("Error: unable to merge formula 2 into view selection 
formula.\n");
        goto Exit;
    }


/*
 * Get the size of the merged formula.
 */

    sError = NSFFormulaGetSize( hSelFormula, &wSelFormulaLen );
    if (sError)
    {
        printf("Error: unable to get size of selection formula.\n" );
        goto Exit;
    }


/*
 * Append the selection formula item to the view note.
 */

    sError = NSFItemAppend( hNote,
                            ITEM_SUMMARY,
                            VIEW_FORMULA_ITEM,
                            (WORD) strlen(VIEW_FORMULA_ITEM),
                            TYPE_FORMULA,
                            OSLockObject(hSelFormula),
                            (DWORD) wSelFormulaLen);

    OSUnlockObject( hSelFormula );


```
**See Also :**
[NSFFormulaCompile](/reference/Func/NSFFormulaCompile)
[NSFFormulaDecompile](/reference/Func/NSFFormulaDecompile)
[NSFFormulaGetSize](/reference/Func/NSFFormulaGetSize)
[NSFFormulaSummaryItem](/reference/Func/NSFFormulaSummaryItem)
---
