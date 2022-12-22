




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



**Data Type : Views**



**VIEW\_TABLE\_FORMAT3** **-** Contains
additional view format information for Domino R5 and Notes/Domino 6.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct  

    {  

    WORD Length;                                 /\*      Length of this
structure \*/  

    DWORD Flags;                                 /\*      Reserved for future
use \*/  

    COLOR\_VALUE BackgroundColor;          /\*      V5 background color \*/  

    COLOR\_VALUE AlternateBackgroundColor;        /\*      V5 alternate row color
\*/  

    COLOR\_VALUE GridColorValue;                  /\*  V6 View's grid color (3
words)\*/  

    WORD wViewMarginTop;                         /\*  V6 View Margin top \*/  

    WORD wViewMarginLeft;                 /\*  V6 View Margin left \*/  

    WORD wViewMarginRight;                /\*  V6 View Margin right \*/  

    WORD wViewMarginBottom;                      /\*  V6 View Margin bottom \*/  

    COLOR\_VALUE MarginBackgroundColor;           /\*  V6 View Margin Background
Color \*/  

    COLOR\_VALUE HeaderBackgroundColor;           /\*      V6 View column header
background color \*/  

    WORD wViewMarginTopUnder;                    /\*  V6 View Margin top --
under header \*/


        COLOR\_VALUE
UnreadColor;                     /\*  V6 unread row color \*/  

        COLOR\_VALUE TotalsColor;                     /\*  V6 Column Total Color
\*/  

        WORD  wMaxRows;                              /\*  V7 Query View Max Row
Limit \*/  

        WORD  wReserved;                             /\*      Reserved for
future use \*/                 

        DWORD dwReserved[1];                         /\*      Reserved for
future use \*/          

        } VIEW\_TABLE\_FORMAT3;


 


**Description :**



This
structure contains view format information for views saved in Domino Release 5
and later. This structure is one of the components of a $VIEWFORMAT item in a
view note. 


 


      All
view notes contain a $VIEWFORMAT item (also known as a "View Table
Format" item).  A $VIEWFORMAT item is an item of TYPE\_VIEW\_FORMAT with
item name VIEW\_VIEW\_FORMAT\_ITEM. The item value of a $VIEWFORMAT item consists
of a single VIEW\_TABLE\_FORMAT structure, followed by one VIEW\_COLUMN\_FORMAT
structure for each column, followed by an item name/formula/column title set
for each column, followed by a VIEW\_TABLE\_FORMAT2 structure, followed by one
VIEW\_COLUMN\_FORMAT2 structure for each column, followed by a VIEW\_TABLE\_FORMAT3
structure.


 


The fields
in this record are:


 


Length -
Length of this record


     Flags -
See VTF3\_xxx                   

BackgroundColor - R5 background color  

AlternateBackgroundColor - R5 alternate row color  

GridColorValue - Notes/Domino 6 grid color


      wViewMarginTop
- Notes/Domino 6 view margin top  

wViewMarginLeft - Notes/Domino 6 view margin left  

wViewMarginRight - Notes/Domino 6 view margin right  

wViewMarginBottom - Notes/Domino 6 view margin bottom  

MarginBackgroundColor - Notes/Domino 6 view margin background color   

HeaderBackgroundColor - Notes/Domino 6 view column HeaderBackgroundColor   

wViewMarginTopUnder - View Margin top -- under header   

UnreadColor -  Notes/Domino 6 unread row color   

TotalsColor - Notes/Domino 6 Column Total Color 


       
wMaxRows - Notes/Domino 7 Query view maximum row limit.  

dwReserved[2] - Reserved for future use 


 **See Also :**


**[VTF3\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DBC0D758B99F951B85256A2C0060495A)**



----------------------------------------------------------------------------------------------------------


 





