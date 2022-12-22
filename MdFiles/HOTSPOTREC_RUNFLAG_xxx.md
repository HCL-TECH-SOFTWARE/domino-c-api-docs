




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Symbolic Value : Hotspot**



**HOTSPOTREC\_RUNFLAG\_xxx** **-** CDHOTSPOTBEGIN
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      HOTSPOTREC\_RUNFLAG\_BEGIN   -  Signals the beginning of a
hotspot.  

  

      HOTSPOTREC\_RUNFLAG\_END      -  Signals the end of a hotspot.  

  

      HOTSPOTREC\_RUNFLAG\_BOX      -  Display a box around the popup.  

  

      HOTSPOTREC\_RUNFLAG\_NOBORDER      -  Do not display a box around the
popup.  

  

      HOTSPOTREC\_RUNFLAG\_FORMULA         -  The text associated with a popup is
generated using a formula.  

  

      HOTSPOTREC\_RUNFLAG\_MOVIE   -  File is a QuickTime movie.  

  

      HOTSPOTREC\_RUNFLAG\_IGNORE            -  Run is for backward compatibility
(i.e. ignore the run).  

  

      HOTSPOTREC\_RUNFLAG\_ACTION            -  Hot region executes a canned
action.  

  

      HOTSPOTREC\_RUNFLAG\_SCRIPT             -  Hot region executes a script.  

  

      HOTSPOTREC\_RUNFLAG\_INOTES             -  Hotspot is a URL and will bring
up the appropriate web page.  

  

      HOTSPOTREC\_RUNFLAG\_ISMAP   -  Contains hot regions that map to different
URLs.  

  

      HOTSPOTREC\_RUNFLAG\_INOTES\_AUTO             -  A hotspot generated automatically
during document load when a document has a text stream that is recognizable as
a URL.  

  

      HOTSPOTREC\_RUNFLAG\_ISMAP\_INPUT   -  Not currently used  

  

      HOTSPOTREC\_RUNFLAG\_SIGNED            -  Hotspot contains signature.  

  

      HOTSPOTREC\_RUNFLAG\_ANCHOR           -  Not currently used  

  

      HOTSPOTREC\_RUNFLAG\_COMPUTED      -  Hotspot is computed text.  

  

      HOTSPOTREC\_RUNFLAG\_TEMPLATE       -  Used in conjunction with embedded
navigator panes.  

  

      HOTSPOTREC\_RUNFLAG\_HIGHLIGHT       -  Hotspot is highlighted.  

  

      HOTSPOTREC\_RUNFLAG\_EXTACTION      -  Hot Region executes an extended
action.  

  

      HOTSPOTREC\_RUNFLAG\_NAMEDELEM    -  Hot link to a named element.  

  

      HOTSPOTREC\_RUNFLAG\_WEBJAVASCRIPT         -  Allow Notes/Domino 6 dual
action type buttons (e.g. client LotusScript, web JS.)  

  

      HOTSPOTREC\_RUNFLAG\_ODSMASK         -  Mask for flag bits actually stored
on disk. In addition, the flag bits HOTSPOTREC\_RUNFLAG\_BEGIN and
HOTSPOTREC\_RUNFLAG\_END are also stored on disk.  

  




**Description :**



These flags
are used to define some of the attributes of a popup in a rich text field.


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





