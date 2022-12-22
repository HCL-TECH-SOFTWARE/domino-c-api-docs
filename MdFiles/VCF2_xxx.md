




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



**VCF2\_xxx** **-** VIEW\_COLUMN\_FORMAT
- Flags2


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VCF2\_S\_DisplayAlignment    -  (Shift) Display alignment (see
VIEW\_COL\_ALIGN\_xxx).  

  

      VCF2\_M\_DisplayAlignment   -  (Mask) Display alignment (see
VIEW\_COL\_ALIGN\_xxx).  

  

      VCF2\_S\_SubtotalCode          -  (Shift) Subtotal code (see NIF\_STAT\_xxx).  

  

      VCF2\_M\_SubtotalCode         -  (Mask) Subtotal code (see NIF\_STAT\_xxx).  

  

      VCF2\_S\_HeaderAlignment    -  (Shift) Header alignment (see VIEW\_COL\_ALIGN\_xxx).  

  

      VCF2\_M\_HeaderAlignment   -  (Mask) Header alignment (see
VIEW\_COL\_ALIGN\_xxx).  

  

      VCF2\_S\_SortPermute           -  (Shift) Make column permuted if
multi-valued.  

  

      VCF2\_M\_SortPermute          -  (Mask) Make column permuted if
multi-valued.  

  

      VCF2\_S\_SecondResortUniqueSort    -  (Shift) Secondary resort column props
different from column def.  

  

      VCF2\_M\_SecondResortUniqueSort   -  (Mask) Secondary resort column props
different from column def.  

  

      VCF2\_S\_SecondResortCategorized   -  (Shift) Secondary resort column
categorized.  

  

      VCF2\_M\_SecondResortCategorized              -  (Mask) Secondary resort
column categorized.  

  

      VCF2\_S\_SecondResortPermute        -  (Shift) Secondary resort column
permuted.  

  

      VCF2\_M\_SecondResortPermute       -  (Mask) Secondary resort column
permuted.  

  

      VCF2\_S\_SecondResortPermutePair              -  (Shift) Secondary resort
column pairwise permuted.  

  

      VCF2\_M\_SecondResortPermutePair             -  (Mask) Secondary resort
column pairwise permuted.  

  

      VCF2\_S\_ShowValuesAsLinks           -  (Shift) Show values as links when
viewed by web browsers.  

  

      VCF2\_M\_ShowValuesAsLinks           -  (Mask) Show values as links when
viewed by web browsers.  

  

      VCF2\_S\_DisplayReadingOrder          -  (Shift) Display reading order (see
VIEW\_COL\_xxx(2)).  

  

      VCF2\_M\_DisplayReadingOrder         -  (Mask) Display reading order (see
VIEW\_COL\_xxx(2)).  

  

      VCF2\_S\_HeaderReadingOrder          -  (Shift) Header reading order (see
VIEW\_COL\_xxx(2)).  

  

      VCF2\_M\_HeaderReadingOrder         -  (Mask) Header reading order (see
VIEW\_COL\_xxx(2)).  

  




**Description :**



The Flags2
field of the VIEW\_COLUMN\_FORMAT structure is a WORD bit field of view column
attributes.  The Shift flags specify the first bit position for a specific
attribute.  The Mask flags specify the bit mask (which bits are used) for a
specific attribute.


 **See Also :**


**[NIF\_STAT\_xxx](NIF_STAT_xxx.md)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_COL\_ALIGN\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/41EA058CA560D4F98525623D00646D94)**



----------------------------------------------------------------------------------------------------------


 





