




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



**CDCAPTION** **-** Text to
display with an object (e.g., a graphic)


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG       
Header;       /\* Tag and length \*/


   WORD       
wLength;      /\* Text length \*/


   BYTE       
Position;     /\* One of the position flags above \*/


   FONTID     
FontID;       /\* Font to use for the text \*/


   COLOR\_VALUE
FontColor;    /\* RGB font color info \*/


   BYTE       
Reserved[11]; /\* Reserved for future use \*/


/\* The 8-bit text
string follows... \*/


} CDCAPTION;


 


**Description :**



This CD
record defines the properties of a caption for a grapic record.  The actual
caption text follows the fixed part of the record.


 


WSIG                     Header             Signature
and length


WORD                   wLength           Caption
text length


BYTE                     Position see
CAPTION\_POSITION\_xxx  


FONTID                 FontID              Font
to use for the text


COLOR\_VALUE     FontColor         RGB
font color information


BYTE                     Reserved[11]


 **See Also :**


**[CAPTION\_POSITION\_xxx](CAPTION_POSITION_xxx.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[FONTID](FONTID.md)**



----------------------------------------------------------------------------------------------------------


 





