




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



**Symbolic Value : Rich Text**



**CDPRETABLE\_xxx** **-** Flag
defintions to CDPRETABLEBEGIN.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDPRETABLE\_AUTO\_CELL\_WIDTH            -  Cell widths are
calculated automatically. If CDPRETABLE\_WIDTHSAMEASWINDOW is not also set, the
table width is set to "Fit with margins."  

  

      CDPRETABLE\_DONTWRAP            -  Wrap text around the table.  

  

      CDPRETABLE\_DROPSHADOW       -  Border effect is set to "Drop
shadow."  

  

      CDPRETABLE\_FIELDDRIVEN          -  Which row to display is field driven -
rows are to be switched programmatically.  

  

      CDPRETABLE\_V4SPACING             -  Use R4 spacing within the table so
that the table is compatible with R4.  

  

      CDPRETABLE\_USEBORDERCOLOR           -  Use a cell border color.  

  

      CDPRETABLE\_WIDTHSAMEASWINDOW    -  Table width is set to fit to window.  

  

      CDPRETABLE\_SHOWTABS             -  Set flags to create a tabbed table
with the tabs on the top of the table. CDPRETABLE\_FIELDDRIVEN must also be set.
Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER\_TABS.  

  

      CDPRETABLE\_SHOWTABSONLEFT            -  Set flags to create a tabbed
table with the tabs on the left side of the table. CDPRETABLE\_FIELDDRIVEN must
also be set. Also set the CDPRETABLEBEGIN ViewerType member to
CDTABLEVIEWER\_TABS.  

  

      CDPRETABLE\_SHOWTABSONBOTTOM     -  Set flags to create a tabbed table
with the tabs on the bottom of the table. CDPRETABLE\_FIELDDRIVEN must also be
set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER\_TABS.  

  

      CDPRETABLE\_SHOWTABSONRIGHT         -  Set flags to create a tabbed table
with the tabs on the right side of the table. CDPRETABLE\_FIELDDRIVEN must also
be set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER\_TABS.  

  




 **See Also :**


**[CDPRETABLEBEGIN](CDPRETABLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





