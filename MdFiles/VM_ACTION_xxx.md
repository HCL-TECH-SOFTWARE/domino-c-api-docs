




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




**Initial Release 4.1**



**Symbolic Value : Navigators**



**VM\_ACTION\_xxx** **-** Navigator
action codes.


**----------------------------------------------------------------------------------------------------------**



**#include <vmods.h>**


 **Symbolic Values :**      VM\_ACTION\_NONE             -  Take no action.  

  

      VM\_ACTION\_SWITCHVIEW             -  Open a view.  

  

      VM\_ACTION\_SWITCHNAV   -  Open another Navigator.  

  

      VM\_ACTION\_ALIAS\_FOLDER          -  Serve as an alias for a Folder.  

  

      VM\_ACTION\_GOTO\_LINK   -  Open a link.  

  

      VM\_ACTION\_RUNSCRIPT   -  Run a LotusScript script.  

  

      VM\_ACTION\_RUNFORMULA           -  Run a formula.  

  

      VM\_ACTION\_GOTO\_URL    -  Go to a URL  

  




**Description :**



These codes
identify the action to be performed when the user selects a graphical element
in a Navigator.  These values are stored in the ClickAction field of the
VIEWMAP\_ACTION\_RECORD.


 **See Also :**


**[VIEWMAP\_ACTION\_RECORD](VIEWMAP_ACTION_RECORD.md)**



----------------------------------------------------------------------------------------------------------


 





