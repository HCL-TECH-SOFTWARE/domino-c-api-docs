




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



**BARREC\_AUTO\_xxx** **-** CDBAR -
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BARREC\_AUTO\_EXP\_READ            -  Expand when reading.  

  

      BARREC\_AUTO\_EXP\_PRE              -  Expand when previewing.  

  

      BARREC\_AUTO\_EXP\_EDIT             -  Expand when editing.  

  

      BARREC\_AUTO\_EXP\_PRINT           -  Expand when printing.  

  

      BARREC\_AUTO\_EXP\_MASK           -  Mask for the auto expand flags.  

  

      BARREC\_AUTO\_COL\_READ           -  Collapse when reading.  

  

      BARREC\_AUTO\_COL\_PRE              -  Collapse when previewing.  

  

      BARREC\_AUTO\_COL\_EDIT             -  Collapse when editing.  

  

      BARREC\_AUTO\_COL\_PRINT          -  Collapse when printing.  

  

      BARREC\_AUTO\_COL\_MASK           -  Mask for the auto collapse flags.  

  

      BARREC\_AUTO\_PRE\_MASK           -  Used to determine whether it is
expanded or collapsed for preview mode.  

  

      BARREC\_AUTO\_READ\_MASK         -  Used to determine whether it is expanded
or collapsed for read mode.  

  

      BARREC\_AUTO\_EDIT\_MASK          -  Used to determine whether it is
expanded or collapsed for preview mode.  

  

      BARREC\_AUTO\_PRINT\_MASK        -  Used to determine whether it is expanded
or collapsed for preview mode.  

  

      BARREC\_AUTO\_ED\_SHIFT             -  Used to shift the flags 12 bits to
check the editor flags.  

  

      BARREC\_AUTO\_ED\_EXP\_READ     -  Used in the BARREC\_AUTO\_READ\_MASK.  

  

      BARREC\_AUTO\_ED\_EXP\_PRE        -  Used in the BARREC\_AUTO\_PRE\_MASK.  

  

      BARREC\_AUTO\_ED\_EXP\_EDIT       -  Used in the BARREC\_AUTO\_EDIT\_MASK.  

  

      BARREC\_AUTO\_ED\_EXP\_PRINT    -  Used in the BARREC\_AUTO\_PRINT\_MASK.  

  

      BARREC\_AUTO\_ED\_EXP\_MASK     -  Unused  

  

      BARREC\_AUTO\_ED\_COL\_READ     -  Used in the BARREC\_AUTO\_READ\_MASK.  

  

      BARREC\_AUTO\_ED\_COL\_PRE       -  Used in the BARREC\_AUTO\_PRE\_MASK.  

  

      BARREC\_AUTO\_ED\_COL\_EDIT      -  Used in the BARREC\_AUTO\_EDIT\_MASK.  

  

      BARREC\_AUTO\_ED\_COL\_PRINT    -  Used in the BARREC\_AUTO\_PRINT\_MASK.  

  

      BARREC\_AUTO\_ED\_COL\_MASK     -  Unused  

  

      BARREC\_AUTO\_ED\_PRE\_MASK     -  Checks if either expanded or collapsed has
been set for preview mode.  

  

      BARREC\_AUTO\_ED\_READ\_MASK   -  Checks if either expanded or collapsed has
been set for read mode.  

  

      BARREC\_AUTO\_ED\_EDIT\_MASK    -  Checks if either expanded or collapsed has
been set for edit mode.  

  

      BARREC\_AUTO\_ED\_PRINT\_MASK             -  Checks if either expanded or
collapsed has been set for print mode.  

  




**Description :**



On-disk
flags for CDBAR (Collapsible Sections)


 **See Also :**


**[CDBAR](CDBAR.md)**



----------------------------------------------------------------------------------------------------------


 





