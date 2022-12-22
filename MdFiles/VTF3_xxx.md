




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



**Symbolic Value : Composite Data;
Rich Text**



**VTF3\_xxx** **-** VIEW\_TABLE\_FORMAT3
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VTF3\_S\_GridStyleSolid         -  (Shift) View grid lines use
solid line.  

  

      VTF3\_M\_GridStyleSolid        -  (Mask) View grid lines use solid line.  

  

      VTF3\_S\_GridStyleDash        -  (Shift) View grid lines use dashes.  

  

      VTF3\_M\_GridStyleDash        -  (Mask) View grid lines use dashes.  

  

      VTF3\_S\_GridStyleDot           -  (Shift) View grid lines use dots.  

  

      VTF3\_M\_GridStyleDot          -  (Mask) View grid lines use dots.  

  

      VTF3\_S\_GridStyleDashDot   -  (Shift) View grid lines use dashes and dots.  

  

      VTF3\_M\_GridStyleDashDot   -  (Mask) View grid lines use dashes and dots.  

  

      VTF3\_S\_AllowCustomizations           -  (Shift) View customizations
on/off .  

  

      VTF3\_M\_AllowCustomizations          -  (Mask) View customizations on/off
.  

  

      VTF3\_S\_EvaluateActionsHideWhen   -  (Shift) View actions evaluate hide
when.  

  

      VTF3\_M\_EvaluateActionsHideWhen              -  (Mask) View actions
evaluate hide when.  

  

      VTF3\_S\_HideLeftMarginBorder         -  (Shift) Hide border after left
margin.  

  

      VTF3\_M\_HideLeftMarginBorder         -  (Mask) Hide border after left
margin.  

  

      VTF3\_S\_BoldUnreadRows    -  (Shift) Bold the unread rows.  

  

      VTF3\_M\_BoldUnreadRows    -  (Mask) Bold the unread rows.  

  

      VTF3\_S\_AllowCreateNewDoc           -  (Shift) Inviewedit-newdocs in view.  

  

      VTF3\_M\_AllowCreateNewDoc           -  (Mask) Inviewedit-newdocs in view.  

  

      VTF3\_S\_HasBackgroundImage         -  (Shift) View has background image.  

  

      VTF3\_M\_HasBackgroundImage        -  (Mask) View has background image.  

  

      VTF3\_S\_MaxRowsLimit        -  (Shift) Limit the maximum rows returned for
a Query View.  

  

      VTF3\_M\_MaxRowsLimit       -  (Mask) Limit the maximum rows returned for a
Query View.  

  




**Description :**



The Flags
field of the VIEW\_TABLE\_FORMAT3 structure is a DWORD bit field of view table
attributes.  The Shift flags specify the first bit position for a specific
attribute.  The Mask flags specify the bit mask (which bits are used) for a
specific attribute.


 **See Also :**


**[VIEW\_TABLE\_FORMAT3](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5E0EE14B6BBE3DC8525667800704EF7)**



----------------------------------------------------------------------------------------------------------


 





