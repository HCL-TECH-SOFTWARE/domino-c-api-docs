




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



**Data Type : Composite Data; Rich
Text**



**CDBACKGROUNDPROPERTIES** **-** Specifies
box background data.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      BSIG Header;  

      BYTE Repeat;               /\*         one of REPEAT\_ (see above) \*/  

      BYTE bReserved;  

      LENGTH\_VALUE lvReservedX;  

      LENGTH\_VALUE lvReservedY;  

      DWORD dwReserved[4];  

      } CDBACKGROUNDPROPERTIES;


 


**Description :**



This CD
Record gives information pertaining to Background Properties for a box. A
CDBACKGROUNDPROPERTIES record may be encapsulated within a CDBEGINRECORD and
CDENDRECORD.  


 


Header                   Identifies
the record as a CDBACKGROUNDPROPERTIES.


Repeat                   see
REPEAT\_xxx 


bReserved              Not
Used.


lvReservedX           Not
Used.


lvReservedY           Not
Used.


dwReserved           Not
Used.


 


 **See Also :**


**[CDBACKGROUNDPROPERTIES\_VERSION1](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/97F01C273560105D8525698300526E0A)**


**[CDBEGINRECORD](CDBEGINRECORD.md)**


**[CDBOXSIZE](CDBOXSIZE.md)**


**[CDENDRECORD](CDENDRECORD.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





