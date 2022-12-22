




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




**Initial Release 4.5**



**Symbolic Value : Rich Text**



**CDTABLECELL\_xxx** **-** CDTABLECELL
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDTABLECELL\_USE\_BKGCOLOR   -  A cell background color is
specified.  

  

      CDTABLECELL\_USE\_V42BORDERS            -  The table was created with
Domino or Notes Release 4.5 or later and contains border width information not
available in previous releases.  

  

      CDTABLECELL\_INVISIBLEH            -  Set if this cell is one of a group
of merged cells, is spanned (made invisible) and is in the same row as the cell
that is doing the spanning.  

  

      CDTABLECELL\_INVISIBLEV            -  Set if this cell is one of a group
of merged cells, is spanned (made invisible) and is not in the same row as the
cell that is doing the spanning.  

  

      CDTABLECELL\_USE\_GRADIENT    -  The cell background uses a top to bottom
gradient.  

  

      CDTABLECELL\_VALIGNCENTER     -  Align cell contents vertically to the
center.  

  

      CDTABLECELL\_GRADIENT\_LTR     -  The cell background uses a gradient left
to right gradient.  

  

      CDTABLECELL\_VALIGNBOTTOM    -  Align cell contents vertically to the
bottom.  

  

      CDTABLECELL\_COLUMN\_HEADER             -  The cell column header.  

  

      CDTABLECELL\_ROW\_HEADER       -  The cell row header.  

  




**Description :**



Flags that
further describe a cell in a table.


 **See Also :**


**[CDTABLECELL](CDTABLECELL.md)**



----------------------------------------------------------------------------------------------------------


 





