




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Data Type : Composite Data; Rich
Text**



**CDACTIONBAREXT** **-** Action bar
attributes.


**----------------------------------------------------------------------------------------------------------**



**#include
<actods.h>**



**Definition :**



typedef struct {


        WSIG           Header;


        COLOR\_VALUE    BackColor;


        COLOR\_VALUE    LineColor;


        COLOR\_VALUE    FontColor;


        COLOR\_VALUE    ButtonColor;


        WORD           BtnBorderDisplay;


        WORD           wAppletHeight;         /\*
This is always recalculated on save \*/


        WORD           wBarBackgroundRepeat;  /\*
See ACTION\_BAR\_BACKGROUND\_xxx types. \*/


        BYTE           BtnWidthStyle;


        BYTE           BtnTextJustify;


        WORD           wBtnWidthAbsolute;     /\*
Valid only if BtnWidthStyle is ACTIONBAR\_BUTTON\_WIDTH\_ABSOLUTE \*/


        WORD           wBtnInternalMargin;    /\*
Extra margin on the inside right and 


                                                       
left edges of a button to space image and text away from 


                                                       
the right and left edges. \*/


        DWORD          dwFlags;                      /\*
See ACTIONBAREXT\_xxx flags \*/


        FONTID  barFontID;                    /\*
Used in conjunction with barHeight \*/


        LENGTH\_VALUE
barHeight;


        DWORD          Spare[12];


        /\*
Leaving many spares for future mouse down/ mouse over colors and whatever else
we want \*/


}       CDACTIONBAREXT;


 


**Description :**



This CD
record defines the Action Bar attributes.  It is an extension of the
CDACTIONBAR record.  It is found within a **$V5ACTIONS** item and is
preceded by a CDACTIONBAR record.


 


The fields
in this record are:


 


Header
- Signature and Length of this CD record


BackColor
- Background color of action bar


LineColor
- Color of action bar bottom border (this "old" border style has been
deprecated in Notes/Domino 6)


FontColor
- Font color of text on action buttons 


ButtonColor
- Background color of action butons


BtnBorderDisplay
- Border display properties of action buttons, see ACTION\_SET\_3D\_xxx


wAppletHeight
- Applet height. This is always recalculated on save


wBarBackgroundRepeat
- See ACTION\_BAR\_BACKGROUND\_xxx types


BtnWidthStyle
-  See ACTIONBAR\_BUTTON\_WIDTH\_xxx


BtnTextJustify
-  See ACTIONBAR\_BUTTON\_TEXT\_


wBtnWidthAbsolute
- Reflects the fixed width of an action button if BtnWidthStyle member is set
to ACTIONBAR\_BUTTON\_WIDTH\_ABSOLUTE


wBtnInternalMargin
- Extra margin on the inside right and left edges of a button to space image
and text away from the right and left edges


dwFlags
- See ACTIONBAREXT\_xxx flags


barFontID
- Used in conjunction with barHeight


barHeight


Spare[12]


 **See Also :**


**[ACTIONBAR\_BACKGROUND\_xxx](ACTIONBAR_BACKGROUND_xxx.md)**


**[ACTIONBAR\_BUTTON\_TEXT\_](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/91982AAC38EBDD4985256A2A0060FB4D)**


**[ACTIONBAR\_BUTTON\_WIDTH\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DAF3EA76F0C4D93E85256A2A0060FB4C)**


**[ACTION\_SET\_3D\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7DB1D608B7ED768085256A2A006244A7)**


**[CDACTION](CDACTION.md)**


**[CDACTIONBAR](CDACTIONBAR.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**



----------------------------------------------------------------------------------------------------------


 





