




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



**EC\_FLAG\_xxx** **-** Control
Flags for an Embedded Control


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      EC\_FLAG\_UNITS     -  Width/Height units  

  

      EC\_FLAG\_DIALOGUNITS    -  Width/Height are in dialog units, not twips.  

  

      EC\_FLAG\_FITTOCONTENTS           -  Width/Height should be adjusted to fit
contents.  

  

      EC\_FLAG\_ALWAYSACTIVE             -  This control is active regardless of
document's R/W status.  

  

      EC\_FLAG\_FITTOWINDOW   -  Let placeholder automatically fit to window.  

  

      EC\_FLAG\_POSITION\_TOP   -  Position control to top of paragraph.  

  

      EC\_FLAG\_POSITION\_BOTTOM       -  Position control to bottom of paragraph.  

  

      EC\_FLAG\_POSITION\_ASCENT        -  Position control to baseline of
paragraph.  

  

      EC\_FLAG\_POSITION\_HEIGHT        -  Position control to height of
paragraph.  

  




 **See Also :**


**[CDEMBEDDEDCTL](CDEMBEDDEDCTL.md)**


**[EC\_DIALOGUNITS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D790B8E7E87556CA8525672E00773EE2)**


**[EC\_FITTOCONTENTS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2C6E6F95BF35FAF48525672E00782BE2)**



----------------------------------------------------------------------------------------------------------


 





