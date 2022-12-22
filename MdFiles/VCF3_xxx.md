




<!--
 /\* Font Definitions \*/
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




**Initial Release 5.0**



**Symbolic Value : Constants; Views**



**VCF3\_xxx** **-** VIEW\_COLUMN\_FORMAT2
- Flags3


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VCF3\_S\_FlatInV5     -  (Shift) View is flat in V5 or
greater.  

  

      VCF3\_M\_FlatInV5     -  (Mask) View is flat in V5 or greater.  

  

      VCF3\_S\_CaseSensitiveSortInV5       -  (Shift) Case Sensitive sorting.  

  

      VCF3\_M\_CaseSensitiveSortInV5       -  (Mask) Case Sensitive sorting.  

  

      VCF3\_S\_AccentSensitiveSortInV5     -  (Shift) Accent Sensitive sorting.  

  

      VCF3\_M\_AccentSensitiveSortInV5   -  (Mask) Accent Sensitive sorting.  

  

      VCF3\_S\_HideWhenFormula              -  (Shift) Column has hide/when
formula set.  

  

      VCF3\_M\_HideWhenFormula              -  (Mask) Column has hide/when
formula set.  

  

      VCF3\_S\_TwistieResource     -  (Shift) Column has twistie resource.  

  

      VCF3\_M\_TwistieResource    -  (Mask) Column has twistie resource.  

  

      VCF3\_S\_Color          -  (Shift) Column value to be used as a color for
this entry.  

  

      VCF3\_M\_Color         -  (Mask) Column value to be used as a color for
this entry.  

  

      VCF3\_ExtDate          -  Column has extended date info.  

  

      VCF3\_NumberFormat           -  Column has extended number format.  

  

      VCF3\_S\_IsColumnEditable    -  (Shift) Can this column be edited.  

  

      VCF3\_M\_IsColumnEditable   -  (Mask) Can this column be edited.  

  

      VCF3\_S\_UserDefinableColor             -  (Shift) User definable color.  

  

      VCF3\_M\_UserDefinableColor            -  (Mask) User definable color.  

  

      VCF3\_S\_HideInR5    -  (Shift) Column has hide/when formula set and needs
to be hidden in R5 or before.  

  

      VCF3\_M\_HideInR5   -  (Mask) Column has hide/when formula set and needs to
be hidden in R5 or before.  

  

      VCF3\_S\_NamesFormat         -  (Shift) Column has extended names format.  

  

      VCF3\_M\_NamesFormat        -  (Mask) Column has extended names format.  

  

      VCF3\_S\_HideColumnTitle     -  (Shift) Hide column title from display, but
not from customization.  

  

      VCF3\_M\_HideColumnTitle    -  (Mask) Hide column title from display, but
not from customization.  

  

      VCF3\_S\_IsSharedColumn     -  (Shift) Is this a shared column?  

  

      VCF3\_M\_IsSharedColumn    -  (Mask) Is this a shared column?  

  

      VCF3\_S\_UseSharedColumnFormulaOnly       -  (Shift) Use only the formula
from shared column - let use modify everything else.  

  

      VCF3\_M\_UseSharedColumnFormulaOnly      -  (Mask) Use only the formula
from shared column - let use modify everything else.  

  




**Description :**



The Flags3
field of the VIEW\_COLUMN\_FORMAT2 structure is a WORD bit field of view
attributes.  The Shift flags specify the first bit position for a specific
attribute.  The Mask flags specify the bit mask (which bits are used) for a
specific attribute.


 


 **See Also :**


**[VIEW\_COLUMN\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/868D1214A6E2E199852561C000516B12)**



----------------------------------------------------------------------------------------------------------


 





