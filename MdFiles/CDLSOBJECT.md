




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




**Initial Release 4.6**



**Data Type : Composite Data; Rich
Text**



**CDLSOBJECT** **-** Lotus Script
object code


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


        WSIG Header;


            DWORD   CodeSize;      /\*
Total code size for multiple code segments, for R6 >64k \*/  

   BYTE Reserved[4];


           /\* Lotus
Script object code follows \*/  

} CDLSOBJECT;


 


**Description :**



The CD
record contains Lotus Script object code.  The fields in this record are:


 


Header             Identifies
this record as a CDLSOBJECT structure.


CodeSize          Total
code size for multiple code segments.


Reserved          Reserved; 
must be 0.


 


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**


**[CDLSOBJECT\_R6](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1411E3696A34C0208525697D0064B895)**



----------------------------------------------------------------------------------------------------------


 





