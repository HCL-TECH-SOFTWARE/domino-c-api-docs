




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



**Symbolic Value : Form**



**ACTION\_BAR\_FLAG\_xxx** **-** Flags for
the CDACTIONBAR record


**----------------------------------------------------------------------------------------------------------**



**#include <actods.h>**


 **Symbolic Values :**      ACTION\_BAR\_FLAG\_NO\_SYS\_COLOR       -  Do not use the system
color for the action bar.  

  

      ACTION\_BAR\_FLAG\_ALIGN\_RIGHT            -  Right justify buttons  

  

      ACTION\_BAR\_FLAG\_TRANS\_BUTTONS     -  Buttons are transparent  

  

      ACTION\_BAR\_FLAG\_SYS\_BUTTONS          -  Buttons use system color  

  

      ACTION\_BAR\_FLAG\_BTNBCK\_IMGRSRC   -  Image resource used for button
background  

  

      ACTION\_BAR\_FLAG\_BARBCK\_IMGRSRC   -  Image resource used for bar
background  

  

      ACTION\_BAR\_FLAG\_SET\_PADDING           -  Use the Padding setting instead
of default 2 pixels.  

  

      ACTION\_BAR\_FLAG\_USE\_APPLET             -  Use applet in browser.  

  

      ACTION\_BAR\_FLAG\_SET\_HEIGHT             -  Use Height setting instead of
default ICON\_DEFAULT\_HEIGHT  

  

      ACTION\_BAR\_FLAG\_ABSOLUTE\_HEIGHT   -  If ACTION\_BAR\_FLAG\_SET\_HEIGHT, use
absolute height specified by user.  

  

      ACTION\_BAR\_FLAG\_BACKGROUND\_HEIGHT        -  If
ACTION\_BAR\_FLAG\_SET\_HEIGHT, use background image's height.  

  

      ACTION\_BAR\_FLAG\_SET\_WIDTH   -  Use Width setting instead of default
width.  

  

      ACTION\_BAR\_FLAG\_BACKGROUND\_WIDTH          -  If
ACTION\_BAR\_FLAG\_SET\_WIDTH, use background image's width.  

  

      ACTION\_BAR\_FLAG\_SHOW\_HINKY\_ALWAYS        -  Always show the drop down
hinky if a button has a menu no matter what the border style is.  

  




**Description :**



These flags
are stored in the dwFlags field of the CDACTIONBAR record.


 **See Also :**


**[CDACTIONBAR](CDACTIONBAR.md)**



----------------------------------------------------------------------------------------------------------


 





