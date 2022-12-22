




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



**Symbolic Value : Constants; Rich
Text**



**EMBEDDEDSCHED\_FLAG\_xxx** **-** Flags for
CDEMBEDDEDSCHEDCTL.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      EMBEDDEDSCHED\_FLAG\_USE\_COLORS1             -  If flag is
set, color values for BusyTimeColor, FreeTimeColor, NoData Color,
DataRestrictedColor and GridLineColor contain valid information. Default color
values are used if this flag is not set.  

  

      EMBEDDEDSCHED\_FLAG\_NO\_INITFROMITEMS    -  If flag is set, scheduler info
(participants, appointment start/end time, etc.) is not initialized from item
values on the note.  

  

      EMBEDDEDSCHED\_FLAG\_NO\_REFRESHFROMITEMS       -  If flag is set, scheduler
info is not refreshed from item values on the note when document is
recalculated.  

  

      EMBEDDEDSCHED\_FLAG\_ALLOW\_FILTERING      -  If flag is set, allow
filtering.  

  

      EMBEDDEDSCHED\_FLAG\_USE\_COLORS2             -  Reserved for future use.  

  

      EMBEDDEDSCHED\_FLAG\_NO\_SHOWLEGEND       -  If flag is set, color legend is
not shown.  

  

      EMBEDDEDSCHED\_FLAG\_SHOWINTERVALINDICATOR    -  If flag is set,
appointment interval indicator is shown.  

  

      EMBEDDEDSCHED\_FLAG\_SHOW\_TWISTIES         -  If flag is set, twisties are
shown.  

  

      EMBEDDEDSCHED\_FLAG\_ALLOW\_EDIT\_INPLACE            -  If flag is set,
scheduler can be edited in place.  

  

      EMBEDDEDSCHED\_FLAG\_ATTENDEE\_WIDTH\_DEFINED   -  If flag is set, overall width
of the scheduler is defined.  

  

      EMBEDDEDSCHED\_FLAG\_ATTENDEE\_WIDTH\_FIXED       -  If flag is set, width of
the left side of the control where attendee names are displayed is fixed.  

  

      EMBEDDEDSCHED\_FLAG\_PEOPLE\_INVISIBLE      -  If flag is set,
"people" (or "top") area is not visible in the scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_ROOMS\_VISIBLE          -  If flag is set,
"rooms" (or "middle") area is visible in the scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_RESOURCES\_VISIBLE              -  If flag is set,
"resources" (or "bottom") area is visible in the scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_PEOPLE\_FIXEDHEIGHT            -  If flag is set,
"people" (or "top") area is a fixed height in the
scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_ROOMS\_FIXEDHEIGHT            -  If flag is set,
"rooms" (or "middle") area is a fixed height in the scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_RESOURCES\_FIXEDHEIGHT    -  If flag is set,
"resources" (or "bottom") area is a fixed height in the
scheduler.  

  

      EMBEDDEDSCHED\_FLAG\_ATTENDEE\_LINES\_DEFINED    -  If flag is set,
PeopleLines, RoomsLines and ResourcesLines values in CDEMBEDDEDSCHEDCTL contain
valid data.  

  

      EMBEDDEDSCHED\_FLAG\_RTL\_READING              -  If flag is set, display
schedule from right to left.  

  

      EMBEDDEDSCHED\_FLAG\_NO\_LAUNCH     -  If flag is set, don't launch
scheduler.  

  




**Description :**



Flags for
CDEMBEDDEDSCHEDCTL.


 **See Also :**


**[CDEMBEDDEDSCHEDCTL](CDEMBEDDEDSCHEDCTL.md)**


**[CDPLACEHOLDER](CDPLACEHOLDER.md)**



----------------------------------------------------------------------------------------------------------


 





