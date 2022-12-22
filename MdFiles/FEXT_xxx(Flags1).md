




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




**Initial Release 4.0**



**Symbolic Value : Rich Text**



**FEXT\_xxx (Flags1)** **-** CDEXTFIELD -
Flags1


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      FEXT\_LOOKUP\_EACHCHAR           -  Lookup name as each
character is typed.  

  

      FEXT\_KWSELRECALC         -  Recalc on new keyword selection.  

  

      FEXT\_KWHINKYMINKY       -  Suppress showing field hinky minky.  

  

      FEXT\_AFTERVALIDATION   -  Recalc after validation.  

  

      FEXT\_ACCEPT\_CARET       -  The first field with this bit set will accept
the caret.  

  

      FEXT\_KEYWORD\_COLS\_SHIFT      -  Number of bits to shift the Keyword
Columns sub-field.  

  

      FEXT\_KEYWORD\_COLS\_MASK      -  Bitmask used to read and write the Keyword
Columns sub-field.  

  

      FEXT\_KEYWORD\_FRAME\_3D         -  Display 3D background for keyword
choices.  

  

      FEXT\_KEYWORD\_FRAME\_STANDARD       -  Display simple frame around keyword
choices.  

  

      FEXT\_KEYWORD\_FRAME\_NONE    -  Display no background for keyword choices.  

  

      FEXT\_KEYWORD\_FRAME\_MASK    -  Bitmask used to read and write the Keyword
Frame Type sub-field.  

  

      FEXT\_KEYWORD\_FRAME\_SHIFT   -  Number of bits to shift the Keyword Frame
Type sub-field.  

  

      FEXT\_KEYWORDS\_UI\_COMBO       -  Display keywords in a combo box.  

  

      FEXT\_KEYWORDS\_UI\_LIST            -  Display keywords in a list box.  

  




**Description :**



Flags for
CDEXTFIELD Flags1.  Note that the low word in Flags1 is not used.


 


The Keyword
Columns sub-field specifies the number of columns to be used when displaying
the options in a field of type Keyword as either checkboxes or radio buttons. 
The number of columns ranges from 1 through 8;  the actual field value stored
is (number of columns) - 1.


 


The Frame
Type subfield specifies the type of background when checkbox or radio button
keyword fields are displayed.  "None" means no special background is
displayed.  "Standard" draws an outline around the options. 
"3D" draws a background as a box with 3-dimensional depth cues.


 **See Also :**


**[CDEXTFIELD](CDEXTFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





