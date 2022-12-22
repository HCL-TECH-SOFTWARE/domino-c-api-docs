




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



**Data Type : Rich Text**



**COLOR\_VALUE** **-** Components
defining Color.


**----------------------------------------------------------------------------------------------------------**



**#include
<colorods.h>**



**Definition :**



typedef struct {  

    WORD Flags;  

    BYTE Component1;  

    BYTE Component2;  

    BYTE Component3;  

    BYTE Component4;


 


        /\*
RGB color space   

        \*       Component1 = red;  

        \*       Component2 = green;  

        \*       Component3 = blue;  

        \*       Component4 = unused;  

        \*/  

} COLOR\_VALUE;


 


 


**Description :**



This data
structure defines the three components of an RGB color which consist of a red,
green, and blue color value.


 


Flags                      set
this member to: COLOR\_VALUE\_FLAGS\_xxx


Component1           Red
component value of RGB color.


Component2           Green
component value of RGB color.


Component3           Blue
component value of RGB color.


 


Example of
colors and RGB values: 


 


BLACK                   Component1
= 0           Component2 = 0           Component3 = 0


WHITE                   Component1
= 255        Component2 = 255        Component3 = 255


GRAY                     Component1
= 128        Component2 = 128        Component3 = 128


LT. GREEN            Component1
= 127        Component2 = 255        Component3 = 127


GREEN                  Component1
= 63          Component2 = 128        Component3 = 63


LT. YELLOW          Component1
= 128        Component2 = 128        Component3 = 63


YELLOW                Component1
= 255        Component2 = 255        Component3 = 127


CYAN                     Component1
= 127        Component2 = 255        Component3 = 255


LT. CYAN               Component1
= 63          Component2 = 128        Component3 = 128


RED                       Component1
= 255        Component2 = 0           Component3 = 0


GREEN                  Component1
= 0           Component2 = 255        Component3 = 0


BLUE                     Component1
= 0           Component2 = 0           Component3 = 255


MAGENTA             Component1
= 255        Component2 = 0           Component3 = 255


YELLOW                Component1
= 255        Component2 = 255        Component3 = 0


CYAN                     Component1
= 0           Component2 = 255        Component3 = 255


DK. RED                 Component1
= 128        Component2 = 0           Component3 = 0


DK. GREEN            Component1
= 0           Component2 = 128        Component3 = 0


DK. BLUE               Component1
= 0           Component2 = 0           Component3 = 128


DK. MAGENTA       Component1
= 128        Component2 = 0           Component3 = 128


DK. YELLOW          Component1
= 128        Component2 = 128        Component3 = 0


DK. CYAN              Component1
= 0           Component2 =128         Component3 = 128


 **See Also :**


**[COLOR\_VALUE\_FLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D8886C73BE9807FE85256676003F5054)**



----------------------------------------------------------------------------------------------------------


 





