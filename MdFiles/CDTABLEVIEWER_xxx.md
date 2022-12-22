




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



**Symbolic Value : Constants**



**CDTABLEVIEWER\_xxx** **-** ViewerType
definition in CDPRETABLEBEGIN.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDTABLEVIEWER\_ONCLICK           -  Table is displayed so
that rows can be cycled through upon a mouse click.  

  

      CDTABLEVIEWER\_ONLOADTIMER             -  Table is displayed to cycle
through rows very xxx milliseconds. The number of milliseconds to cycle through
is specified in a CDTIMERINFO structure.  

  

      CDTABLEVIEWER\_ONLOADCYCLEONCE   -  Table is displayed to cycle through
the rows once when opened.  

  

      CDTABLEVIEWER\_TABS     -  Table is displayed with tabs for the user to
select which row to display.  

  

      CDTABLEVIEWER\_FIELDDRIVEN    -  Which row to display is field driven -
rows are to be switched programmatically.  

  

      CDTABLEVIEWER\_CYCLEONCE     -  Table is displayed to cycle through the
rows once via a mouse click.  

  

      CDTABLEVIEWER\_CAPTIONS        -  Table is displayed with window caption
boxes for the user to select which row to display.  

  

      CDTABLEVIEWER\_LAST     -  The highest value for this set of flags.  

  




 **See Also :**


**[CDPRETABLEBEGIN](CDPRETABLEBEGIN.md)**


**[CDTIMERINFO](CDTIMERINFO.md)**



----------------------------------------------------------------------------------------------------------


 





