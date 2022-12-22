




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




**Initial Release 6**



**Symbolic Value : Composite Data;
Hotspot; Rich Text**



**BARREC\_DATA\_BORDER\_xxx** **-** CDDATAFLAGS
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BARREC\_DATA\_BORDER\_MASK    -  Mask used for getting and
setting the data border type.  

  

      BARREC\_DATA\_BORDER\_GRADIENT        -  Box is visible around section title
with shading blended to match the background.  

  

      BARREC\_DATA\_BORDER\_TAB       -  Section is indicated by a tab.  

  

      BARREC\_DATA\_BORDER\_DIAG     -  Section is indicated by a tab with a
diagonal border.  

  




**Description :**



On-disk
flags for CDDATAFLAGS. For collapsible sections indicated by a tab or a tab
with a diagonal border, the CDBAR record (with its Flags member set to
BARREC\_BORDER\_OTHER) is followed by a CDDATAFLAGS structure with its Flags
member set to BARREC\_DATA\_BORDER\_TAB (for tab) or BARREC\_DATA\_BORDER\_DIAG (for
diagonal).


 **See Also :**


**[CDDATAFLAGS](CDDATAFLAGS.md)**



----------------------------------------------------------------------------------------------------------


 





