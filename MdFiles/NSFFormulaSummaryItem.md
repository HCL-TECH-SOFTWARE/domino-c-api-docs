




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



**NSFFormulaSummaryItem** **- Add the
item name of a column to a view note's item name list.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**



STATUS
LNPUBLIC **NSFFormulaSummaryItem(**  

      FORMULAHANDLE  hFormula,  

      const char far \*ItemName,  

      WORD  ItemNameLength**);**



**Description :**



This
function adds the name of a view column to the list of item names  

contained in the view's $FORMULA item.  

  

The definition of a view note contains a  $FORMULA item.  This item is of type   

TYPE\_FORMULA and contains:  

  

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

   

Please refer to the *User Guide* for more information about the structure
of a view note.


 


**Parameters :**



Input :  

hFormula  -  A handle to the formula with which the summary item is to be
associated.  

  

ItemName  -  A far pointer to a character string specifying the name of the
item to be added to the summary buffer.  

  

ItemNameLength  -  The length of the string specifying the item name.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - STATUS returned from a lower level Notes function called in the
action routine and passed back.  

  

  




 **See Also :**


**[NSFFormulaCompile](NSFFormulaCompile.md)**


**[NSFFormulaDecompile](NSFFormulaDecompile.md)**


**[NSFFormulaGetSize](NSFFormulaGetSize.md)**


**[NSFFormulaMerge](NSFFormulaMerge.md)**



----------------------------------------------------------------------------------------------------------


 





