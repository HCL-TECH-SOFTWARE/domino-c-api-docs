




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




**Initial Release 4.0**



**Symbolic Value : Rich Text**



**CDTABLE\_xxx** **-** CDTABLEBEGIN
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDTABLE\_AUTO\_CELL\_WIDTH      -  Cell widths are calculated
automatically. The table width is set to "Fit with margins" or
"Fit to window". Further details are set in the Flags member of the
CDPRETABLEBEGIN structure.  

  

      CDTABLE\_V4\_BORDERS     -  The table was created with R4 or later
releases. The table contains width information that is not found in previous
releases of Notes.  

  

      CDTABLE\_3D\_BORDER\_EMBOSS   -  The table uses embossed cell borders
(groove cell border style).  

  

      CDTABLE\_3D\_BORDER\_EXTRUDE             -  If set, the table uses extruded
cell borders (ridge cell border style).  

  

      CDTABLE\_BIDI\_RTLTABLE             -  The table reading order is right to
left.  

  

      CDTABLE\_ALIGNED\_RIGHT            -  The table position is aligned to the
right.  

  

      CDTABLE\_COLLAPSIBLE    -  Show only one row at a time. Further details
are set in the ViewType member of the CDPRETABLEBEGIN structure.  

  

      CDTABLE\_LEFTTOP            -  Table Color Style is set to Left and Top.  

  

      CDTABLE\_TOP        -  Table Color Style is set to Top.  

  

      CDTABLE\_LEFT       -  Table Color Style is set to Left.  

  

      CDTABLE\_ALTERNATINGCOLS      -  Table Color Style is set to Alternating
Columns.  

  

      CDTABLE\_ALTERNATINGROWS     -  Table Color Style is set to Alternating
Rows.  

  

      CDTABLE\_RIGHTTOP         -  Table Color Style is set to Right and Top.  

  

      CDTABLE\_RIGHT    -  Table Color Style is set to Right  

  

      CDTABLE\_SOLID     -  This flag is used as a bit mask. If all the bits in
this mask are set, then the Table Color Style is set to Solid.  

  

      CDTABLE\_TEMPLATEBITS             -  Bit mask for the various Table Color
Styles.  

  

      CDTABLE\_ALIGNED\_CENTER         -  Table position is aligned in the
center.  

  

      CDTABLE\_TEXTFLOWS      -  Set text to flow from one cell to the next
horizontally.  

  




**Description :**



Flag values
stored in the Flags field of the CDTABLEBEGIN record.


 **See Also :**


**[CDTABLEBEGIN](CDTABLEBEGIN.md)**


**[CDPRETABLEBEGIN](CDPRETABLEBEGIN.md)**


**[CDPRETABLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5AA21676B377ED6A85256677006DDC29)**


**[CDTABLEVIEWER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4E3B71C1BAAEE2EF85256A2A0062F83A)**



----------------------------------------------------------------------------------------------------------


 





