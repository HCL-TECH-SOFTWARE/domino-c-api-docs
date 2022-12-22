




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



**NSFFormulaDecompile** **-
Decompiles a formula from binary form into text form.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**



STATUS
LNPUBLIC **NSFFormulaDecompile(**  

      char far \*pFormulaBuffer,  

      BOOL  fSelectionFormula,  

      DHANDLE far \*rethFormulaText,  

      WORD far \*retFormulaTextLength**);**



**Description :**



This
function accepts a pointer to a compiled selection formula or a compiled column
formula, translates the formula into a LMBCS string, and returns a handle to
the formula string.  The caller is responsible for freeing the memory
associated with this string.  

  

Call OSLockObject to obtain a pointer to the text string.  The string is not
zero terminated.  Call OSUnlockObject when finished accessing the string.  Call
OSMemFree to free the memory associated with the handle.


 


Note that if
you use NSFFormulaDecompile with a compiled view selection formula that was
contructed using NSFFormulaMerge, rethFormulaText will contain only the view
selection formula and not the column formulas.


 


**Parameters :**



Input :  

pFormulaBuffer  -  A pointer to a compiled formula.  

  

fSelectionFormula  -  Set to TRUE if this formula is a selection formula in a
view.  Otherwise set to FALSE.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - STATUS returned from a lower level Notes function called in the
action routine and passed back.  

  

  

rethFormulaText  -  The specified variable receives a handle to the text of the
decompiled formula.  Call OSLock() to get a pointer to the formula text.  

  

retFormulaTextLength  -  The specified variable receives the length of the
formula text.  

  




 **Sample Usage :**


    STATUS      error;  

    DHANDLE      hFormulaText;  

    WORD        wFormulaTextLength;  

    CHAR       \*pcFormulaText;  

    WORD        i;  

  

    if (error = NSFFormulaDecompile( pData, FALSE,   

                &hFormulaText,   

                &wFormulaTextLength ))  

    {  

        fprintf(dumpfile, "  Unable to decompile formula.\n");  

        return;  

    }  

  

    pcFormulaText = (CHAR far \*)OSLockObject(hFormulaText);  

  

    fprintf(dumpfile, "  Decompiled formula = '");  

    for (i=0;i<wFormulaTextLength;i++)   

    {  

        fprintf(dumpfile, "%c", pcFormulaText[i]);  

    }  

    fprintf(dumpfile, "\n");  

    OSUnlockObject(hFormulaText);  

    OSMemFree(hFormulaText);  

  




 **See Also :**


**[NSFFormulaCompile](NSFFormulaCompile.md)**



----------------------------------------------------------------------------------------------------------


 





