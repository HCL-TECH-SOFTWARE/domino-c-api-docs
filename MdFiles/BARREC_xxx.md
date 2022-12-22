




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



**Symbolic Value : Composite Data;
Hotspot; Rich Text**



**BARREC\_xxx** **-** CDBAR -
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BARREC\_DISABLED\_FOR\_NON\_EDITORS             -  Section can
be expanded only if the current user has editing privileges.  

  

      BARREC\_EXPANDED          -  Section is expanded.  

  

      BARREC\_PREVIEW             -  The bar is preview only.  

  

      BARREC\_BORDER\_INVISIBLE        -  Border is not visible around section
title.  

  

      BARREC\_ISFORMULA         -  Bar caption is a formula.  

  

      BARREC\_HIDE\_EXPANDED            -  Caption is hidden when bar is
expanded.  

  

      BARREC\_INTENDED           -  Whether the user can edit this bar or not.  

  

      BARREC\_HAS\_COLOR        -  The bar has an explicit color reference.  

  

      BARREC\_BORDER\_MASK   -  Mask used for getting and setting the border
type.  

  

      BARREC\_BORDER\_SHADOW         -  Draw a shadow around the border of the
bar.  

  

      BARREC\_BORDER\_NONE   -  No default border style.  

  

      BARREC\_BORDER\_SINGLE            -  Bar is single thickness.  

  

      BARREC\_BORDER\_DOUBLE           -  Bar is double thickness.  

  

      BARREC\_BORDER\_TRIPLE             -  Bar is triple thickness.  

  

      BARREC\_BORDER\_TWOLINE         -  Bar is two lines.  

  

      BARREC\_BORDER\_WINDOWCAPTION       -  Shaded box is visible around section
title. Open and close is indicated by icon on right of section.  

  

      BARREC\_BORDER\_OTHER             -  Used to create tab or diagonal sections.
See Description below for more information.  

  

      BARREC\_BORDER\_GRADIENT       -  Box is visible around section title with
shading blended to match the background.  

  

      BARREC\_BORDER\_TAB      -  Section is indicated by a tab.  

  

      BARREC\_BORDER\_DIAG    -  Section is indicated by a tab with a diagonal
border.  

  

      BARREC\_INDENTED           -  Unused  

  

      BARREC\_ODS\_MASK          -  Used to set bits that don't need to be stored
on disk to 0.  

  




**Description :**



On-disk
flags for CDBAR (Collapsible Sections). For collapsible sections indicated by a
tab or a tab with a diagonal border, the CDBAR record (with its Flags member
set to BARREC\_BORDER\_OTHER) is followed by a CDDATAFLAGS structure with its
Flags member set to BARREC\_DATA\_BORDER\_TAB (for tab) or BARREC\_DATA\_BORDER\_DIAG
(for diagonal).


 **See Also :**


**[CDBAR](CDBAR.md)**


**[CDDATAFLAGS](CDDATAFLAGS.md)**



----------------------------------------------------------------------------------------------------------


 





