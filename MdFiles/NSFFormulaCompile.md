




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



**NSFFormulaCompile** **- Compiles
a formula into binary form.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**



STATUS
LNPUBLIC **NSFFormulaCompile(**  

      char far \*FormulaName,  

      WORD  FormulaNameLength,  

      const char far \*FormulaText,  

      WORD  FormulaTextLength,  

      FORMULAHANDLE far \*rethFormula,  

      WORD far \*retFormulaLength,  

      STATUS far \*retCompileError,  

      WORD far \*retCompileErrorLine,  

      WORD far \*retCompileErrorColumn,  

      WORD far \*retCompileErrorOffset,  

      WORD far \*retCompileErrorLength**);**



**Description :**



This
function accepts a LMBCS string containing a formula and translates the formula
into binary form.  Functions that take compiled formulas as parameters include
NSFSearch and NSFComputeStart.  

  

After you use the compiled formula (returned in argument 5) you must deallocate
the buffer that holds the formula.  Do this by calling OSMemFree and passing it
the FORMULAHANDLE.


 


**Parameters :**



Input :  

FormulaName  -  A pointer to a name for this formula. Specify NULL for this
parameter unless the formula is going to be a column formula in a view note; 
in this case, specify the column's item name for this parameter.    

  

FormulaNameLength  -  The length of formula's name.  If the previous parameter
is NULL, set this parameter to 0.   

  

FormulaText  -  A pointer to the LMBCS text of the formula.  

  

FormulaTextLength  -  The length of the formula text.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.  The return codes include:  

  

NOERROR  

ERR\_FORMULA\_COMPILATION  

  

If you receive the second return code, more information about the error is
available in arguments 7 through 11 of the call.  

  

  

rethFormula  -  A pointer to a FORMULAHANDLE that will receive the handle of
the compiled formula  

  

retFormulaLength  -  A pointer to a WORD that will receive the length of the
compiled formula.  

  

retCompileError  -  A pointer to a STATUS that will receive any compilation
error (from translating the character text formula to binary).  

  

retCompileErrorLine  -  A pointer to a WORD that will receive the line number
of any compilation error.  This information is used by the Notes screen interface.  

  

retCompileErrorColumn  -  A pointer to a WORD that will receive the column
number of any compilation error.  This information is used by the Notes screen
interface.  

  

retCompileErrorOffset  -  A pointer to a WORD that will receive the offset
(within the formula) of any compilation error.  You may use this information
within your program to find the error.  

  

retCompileErrorLength  -  A pointer to a WORD that will receive the length of
any compilation error.  You may use this information (with retCompileErrorOffset)
to find the error.  

  




 **Sample Usage :**


  

sError = NSFFormulaCompile( NULL,  

                            0,  

                            szSelFormula,  

                            strlen(szSelFormula),  

                            &hSelFormula,  

                            &wSelFormulaLen,  

                            &wdc, &wdc, &wdc,  

                            &wdc, &wdc );


 **See Also :**


**[OSMemFree](OSMemFree.md)**


**[NSFSearch](NSFSearch.md)**


**[NSFComputeStart](NSFComputeStart.md)**


**[NSFComputeEvaluate](NSFComputeEvaluate.md)**



----------------------------------------------------------------------------------------------------------


 





