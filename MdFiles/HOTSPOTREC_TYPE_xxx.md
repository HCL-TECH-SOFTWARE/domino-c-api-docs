




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



**HOTSPOTREC\_TYPE\_xxx** **-** CDHOTSPOTBEGIN
- Type


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      HOTSPOTREC\_TYPE\_POPUP         -  The hotspot is a popup  

  

      HOTSPOTREC\_TYPE\_HOTREGION            -  The hotspot is a button whose
presentation is an arbitrary region of the rich text field. This region is
bounded by the CDHOTSPOTBEGIN and CDHOTSPOTEND records.  

  

      HOTSPOTREC\_TYPE\_BUTTON      -  The hotspot is a button.  

  

      HOTSPOTREC\_TYPE\_FILE             -  The hotspot is a file attachment.  

  

      HOTSPOTREC\_TYPE\_SECTION     -  The hotspot is a Notes Release 3 section
field hotspot.  

  

      HOTSPOTREC\_TYPE\_ANY             -  Unused.  

  

      HOTSPOTREC\_TYPE\_HOTLINK      -  The hotspot is a document, database, or
view link hotspot. The presentation of this hotspot is an arbitrary region of
the rich text field. This region is bounded by the CDHOTSPOTBEGIN and
CDHOTSPOTEND records.  

  

      HOTSPOTREC\_TYPE\_BUNDLE       -  The hotspot is a standard collapsible
section which is not access controlled.  

  

      HOTSPOTREC\_TYPE\_V4\_SECTION           -  The hotspot is an access
controlled collapsible section.  

  

      HOTSPOTREC\_TYPE\_SUBFORM    -  The hotspot is a subform.  

  

      HOTSPOTREC\_TYPE\_ACTIVEOBJECT       -  The hotspot is an active object.  

  

      HOTSPOTREC\_TYPE\_OLERICHTEXT         -  The hotspot is an OLE rich text
object.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDVIEW     -  The hotspot is an embedded view.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDFPANE   -  The hotspot is an embedded folder
pane.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDNAV       -  The hotspot is an embedded
navigator.  

  

      HOTSPOTREC\_TYPE\_MOUSEOVER           -  The hotspot is mouse over text
popup.  

  

      HOTSPOTREC\_TYPE\_FILEUPLOAD            -  The hotspot is a file upload
placeholder.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDOUTLINE           -  The hotspot is an embedded
outline.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDCTL       -  The hotspot is an embedded control
window.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDCALENDARCTL             -  The hotspot is an
embedded calendar control (date picker).  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDSCHEDCTL       -  The hotspot is an embedded
scheduling control.  

  

      HOTSPOTREC\_TYPE\_RCLINK        -  The hotspot is a resource link.  

  

      HOTSPOTREC\_TYPE\_EMBEDDEDEDITCTL           -  The hotspot is an embedded
editor control.  

  

      HOTSPOTREC\_TYPE\_CONTACTLISTCTL   -  Embeddable buddy list.  

  




**Description :**



These flags
are used to define what type of hotspot is being defined by a CDHOTSPOTBEGIN
data structure.


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





