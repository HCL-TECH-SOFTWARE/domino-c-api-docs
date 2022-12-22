




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




 


**Symbolic Value : Constants; Views**



**VCF1\_xxx** **-** VIEW\_COLUMN\_FORMAT
- Flags1


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VCF1\_S\_Sort            -  (Shift) Add column to sort.  

  

      VCF1\_M\_Sort           -  (Mask) Add column to sort.  

  

      VCF1\_S\_SortCategorize       -  (Shift) Make column a category.  

  

      VCF1\_M\_SortCategorize       -  (Mask) Make column a category.  

  

      VCF1\_S\_SortDescending.     -  (Shift) Sort in descending order (ascending
if FALSE).  

  

      VCF1\_M\_SortDescending     -  (Mask) Sort in descending order (ascending
if FALSE).  

  

      VCF1\_S\_Hidden       -  (Shift) Hidden column.  

  

      VCF1\_M\_Hidden       -  (Mask) Hidden column.  

  

      VCF1\_S\_Response   -  (Shift) Response column.  

  

      VCF1\_M\_Response   -  (Mask) Response column.  

  

      VCF1\_S\_HideDetail   -  (Shift) Do not show detail on subtotaled columns.  

  

      VCF1\_M\_HideDetail              -  (Mask) Do not show detail on subtotaled
columns.  

  

      VCF1\_S\_Icon           -  (Shift) Display icon instead of text.  

  

      VCF1\_M\_Icon           -  (Mask) Display icon instead of text.  

  

      VCF1\_S\_NoResize   -  (Shift) Resizable at run time.  

  

      VCF1\_M\_NoResize   -  (Mask) Resizable at run time.  

  

      VCF1\_S\_ResortAscending    -  (Shift) Resortable in ascending order.  

  

      VCF1\_M\_ResortAscending   -  (Mask) Resortable in ascending order.  

  

      VCF1\_S\_ResortDescending   -  (Shift) Resortable in descending order.  

  

      VCF1\_M\_ResortDescending             -  (Mask) Resortable in descending
order.  

  

      VCF1\_S\_Twistie       -  (Shift) Show twistie if expandable.  

  

      VCF1\_M\_Twistie      -  (Mask) Show twistie if expandable.  

  

      VCF1\_S\_ResortToView         -  (Shift) Resort to a view.  

  

      VCF1\_M\_ResortToView        -  (Mask) Resort to a view.  

  

      VCF1\_S\_SecondResort         -  (Shift) Secondary resort column set.  

  

      VCF1\_M\_SecondResort        -  (Mask) Secondary resort column set.  

  

      VCF1\_S\_SecondResortDescending   -  (Shift) Secondary column resort
descending (ascending if clear).  

  

      VCF1\_M\_SecondResortDescending   -  (Mask) Secondary column resort
descending (ascending if clear).  

  

      VCF1\_S\_CaseInsensitiveSort            -  OBSOLETE - replaced by
VCF3\_S\_CaseSensitiveSortInV5  

  

      VCF1\_M\_CaseInsensitiveSort           -  OBSOLETE - replaced by
VCF3\_M\_CaseSensitiveSortInV5  

  

      VCF1\_S\_AccentInsensitiveSort         -  OBSOLETE - replaced by
VCF3\_S\_AccentSensitiveSortInV5  

  

      VCF1\_M\_AccentInsensitiveSort        -  OBSOLETE - replaced by
VCF3\_M\_AccentSensitiveSortInV5  

  




**Description :**



Possible
optional values for the Flags1 member of the VIEW\_COLUMN\_FORMAT structure. 
These values specify column attributes.


 **See Also :**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





