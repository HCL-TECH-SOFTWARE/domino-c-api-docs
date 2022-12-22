




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




**Initial Release 4.5**



**Symbolic Value : Rich Text**



**FEXT\_xxx (Flags2)** **-** CDEXTFIELD -
Flags2


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      FEXT\_KW\_CHOICE\_RECALC          -  TRUE to recalc the value
choices.  

  

      FEXT\_HTML\_IN\_FIELDDEF             -  An HTML Attribute formula follows
the CDEXTFIELD record.  

  

      FEXT\_HIDEDELIMITERS     -  Set if hiding delimeters.  

  

      FEXT\_KW\_RTL\_READING\_ORDER             -  Right to Left Reading Order.  

  

      FEXT\_ALLOWTABBINGOUT            -  Set if tab will exit field.  

  

      FEXT\_PASSWORD   -  Set if field is a password field.  

  

      FEXT\_USEAPPLETINBROWSER     -  Set if applet should be used for a
browser.  

  

      FEXT\_CONTROL     -  Set if field is a control.  

  

      FEXT\_LITERALIZE   -  Set if this is a formula field which should have
item substitution based on items on the form. This is the counterpart to a
computed formula which is a formula programmatically generated through
@formulas.  

  

      FEXT\_CONTROLDYNAMIC   -  TRUE if field is a dynamic control.  

  

      FEXT\_RUNEXITINGONCHANGE      -  TRUE if should run exiting event when
value changes. Currently only implemented for native date/time.  

  

      FEXT\_TIMEZONE    -  TRUE if this is a time zone field.  

  

      FEXT\_PROPORTIONALHEIGHT      -  TRUE if field has proportional height.  

  

      FEXT\_PROPORTIONALWIDTH        -  TRUE if field has proportional width.  

  

      FEXT\_SHOWIMSTATUS      -  TRUE if a names type field displays im online
status.  

  




**Description :**



These
options are stored in the Flags2 field of the CDEXTFIELD record.


 **See Also :**


**[CDEXTFIELD](CDEXTFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





