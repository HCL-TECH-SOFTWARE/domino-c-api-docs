




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




**Initial Release 4.6**



**Symbolic Value : Form**



**ACTION\_xxx (flags)** **-** CDACTION
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <actods.h>**


 **Symbolic Values :**      ACTION\_SHOW\_IN\_MENU   -  Display in the "Actions"
pull-down menu.  

  

      ACTION\_SHOW\_IN\_BAR     -  Display in the action button bar.  

  

      ACTION\_SHOW\_WHEN\_PREVIEWING        -  Show the action when previewing the
document.  

  

      ACTION\_SHOW\_WHEN\_READING   -  Show the action when reading the document.  

  

      ACTION\_SHOW\_WHEN\_EDITING   -  Show the action when editing the document.  

  

      ACTION\_SHOW\_ON\_OLE\_LAUNCH            -  Show when launching OLE object.  

  

      ACTION\_OLE\_CLOSE\_WHEN\_CHOSEN      -  Close the OLE object when this
action is selected.  

  

      ACTION\_NO\_FORMULA      -  No "hide when" formula is stored for
this action.  

  

      ACTION\_SHOW\_WHEN\_PREVEDITING      -  Show when editing in the preview
window.  

  

      ACTION\_OLE\_DOC\_WINDOW\_TO\_FRONT             -  Bring the OLE document
window to the front when this action is selected.  

  

      ACTION\_HIDE\_FROM\_NOTES        -  Do not display in Notes.  

  

      ACTION\_HIDE\_FROM\_WEB            -  Do not display in Web browsers.  

  

      ACTION\_READING\_ORDER\_RTL    -  Action reading order from right.  

  

      ACTION\_SHARED    -  Action is shared.  

  

      ACTION\_MODIFIED             -  Action has been modified (not saved on
disk).  

  

      ACTION\_ALWAYS\_SHARED            -  Flag not saved on disk.  

  

      ACTION\_ALIGN\_ICON\_RIGHT         -  Right align action button  

  

      ACTION\_IMAGE\_RESOURCE\_ICON            -  Use graphic image icon.  

  

      ACTION\_FRAME\_TARGET   -  Use target frame.  

  

      ACTION\_TEXT\_ONLY\_IN\_MENU     -  Shows only icon in button bar. (Displays
text in the Action menu if ACTION\_SHOW\_IN\_MENU flag is set).  

  

      ACTION\_BUTTON\_TO\_RIGHT         -  Show button on opposite side from
action bar direction.  

  

      ACTION\_SHOW\_IN\_POPUPMENU   -  Show action in pop-up menu.  

  

      ACTION\_HIDE\_FROM\_MOBILE       -  Hide action from mobile users.  

  

      ACTION\_ODS\_FLAG\_MASK             -  Bit mask for the CDACTION flag bits.  

  




**Description :**



Possible
values for the Flags member of the CDACTION structure.  These values further
describe attributes for the action.


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





