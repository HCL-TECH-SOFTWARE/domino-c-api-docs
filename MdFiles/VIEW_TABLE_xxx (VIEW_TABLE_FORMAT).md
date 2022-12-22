




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



**Symbolic Value : Views**



**VIEW\_TABLE\_xxx (VIEW\_TABLE\_FORMAT)** **-** VIEW\_TABLE\_FORMAT
- Flags2


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VIEW\_TABLE\_FLAT\_HEADINGS      -  TRUE if we should display
no-borders at all on the header.  

  

      VIEW\_TABLE\_COLORIZE\_ICONS    -  TRUE if the icons displayed in the view
should be colorized.  

  

      VIEW\_TABLE\_HIDE\_SB       -  TRUE if we should not display a search bar
for this view.  

  

      VIEW\_TABLE\_HIDE\_CAL\_HEADER             -  TRUE if we should hide the
calendar header.  

  

      VIEW\_TABLE\_NOT\_CUSTOMIZED   -  TRUE if view has not been customized (i.e.
not saved by Designer).  

  




**Description :**



These flags
help define the format  used when a view is displayed. The Flags2 word of the
VIEW\_TABLE\_FORMAT structure contains a value constructed by combining these
flags using bitwise-OR.


 **See Also :**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





