




<!--
 /\* Font Definitions \*/
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



**NSFComputeStart** **- Perform
some initialization prior to formula evaluation.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**



STATUS
LNPUBLIC **NSFComputeStart(**  

      WORD  Flags,  

      void far \*lpCompiledFormula,  

      HCOMPUTE far \*rethCompute**);**



**Description :**



This
function takes a pointer to a compiled formula as input and returns an HCOMPUTE
variable as output.  The HCOMPUTE variable is used by Domino and Notes to
uniquely identify the formula being evaluated.  This function MUST be called
before calling NSFComputeEvaluate.


 


**Parameters :**



Input :  

Flags  -  Reserved - must be set to 0;  

  

lpCompiledFormula  -  A far void pointer to a compiled formula (A formula is
compiled by calling NSFFormulaCompile).  On UNIX systems, this parameter must
be word-aligned.  

  




Output :  

(routine)  -    

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

rethCompute  -  A far pointer to an HCOMPUTE variable.  The HCOMPUTE variable
is passed as input to the function NSFComputeEvaluate to identify the formula
to be evaluated.  

  




 **See Also :**


**[NSFComputeEvaluate](NSFComputeEvaluate.md)**


**[NSFComputeStop](NSFComputeStop.md)**



----------------------------------------------------------------------------------------------------------


 





