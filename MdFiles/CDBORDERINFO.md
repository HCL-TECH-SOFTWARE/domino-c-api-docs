




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



**CDBORDERINFO** **-** Structure
defining border information for a table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG Header; /\*
Signature and length of this record \*/


   DWORD       Flags;


   WORD        BorderStyle;


   WORD       
BorderWidthTop;    


   WORD       
BorderWidthLeft;   


   WORD       
BorderWidthBottom; 


   WORD       
BorderWidthRight;  


   DWORD       dwSpare;


   WORD       
BorderFlags;


   WORD       
DropShadowWidth;


   WORD       
InnerWidthTop;     


   WORD       
InnerWidthLeft;    


   WORD       
InnerWidthBottom;  


   WORD       
InnerWidthRight;   


   WORD       
OuterWidthTop;     


   WORD       
OuterWidthLeft;    


   WORD       
OuterWidthBottom;  


   WORD       
OuterWidthRight;   


   COLOR\_VALUE Color;


   WORD       
wSpares[5];


} CDBORDERINFO;


 


**Description :**



This CD
record describes border information for a given table.  This CD record will be
preceded with CD record CDPRETABLEBEGIN both encapsulated between a
CDBEGINRECORD and a CDENDRECORD record with CD record signature
CDPRETABLEBEGIN.


 


CDBEGINRECORD


      CDPRETABLEBEGIN


            CDBORDERINFO


CDENDRECORD


 


 


WSIG                           Header                         Signature
and length of this record


DWORD                       Flags                            Not
Used must be 0


DWORD                       BorderStyle                  CDBORDERSTYLE\_xxx


WORD                         BorderWidthTop            Thickness
Top


WORD                         BorderWidthLeft            Thickness
Left


WORD                         BorderWidthBottom       Thickness
Bottom


WORD                         BorderWidthRight         Thickness
Right


DWORD                       dwSpare


WORD                         BorderFlags                  CDBORDER\_FLAGS\_xxx


WORD                         DropShadowWidth        Border
Effects Drop Shadow Width


WORD                         InnerWidthTop              Inside
Thickness Top


WORD                         InnerWidthLeft              Inside
Thickness Left


WORD                         InnerWidthBottom         Inside
Thickness Bottom


WORD                         InnerWidthRight            Inside
Thickness Right


WORD                         OuterWidthTop             Outside
Thickness Top


WORD                         OuterWidthLeft             Outside
Thickness Left


WORD                         OuterWidthBottom        Outside
Thickness Bottom


WORD                         OuterWidthRight           Outside
Thickness Right


COLOR\_VALUE            Color                            Border
Color


WORD                         wSpares[5]


 


 


 


 **See Also :**


**[CDBORDERSTYLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6976492B58A9EB6485256678004CD4CA)**


**[CDBORDER\_FLAGS\_xxx](CDBORDER_FLAGS_xxx.md)**


**[CDPRETABLEBEGIN](CDPRETABLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





