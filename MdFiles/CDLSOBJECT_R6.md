




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



**CDLSOBJECT\_R6** **-** LotusScript
object code for Notes/Domino 6


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      WSIG   Header;  

#define CDLSOBJECT\_R6\_TYPE  01                     /\* signals multiple code
segments for R6 >64k \*/  

      BYTE    Flags;  

      BYTE   Reserved[7];       

      } CDLSOBJECT\_R6;


 


**Description :**



This CD
record contains Lotus Script object code for Notes/Domino 6.  The fields in
this record are:


 


Header             Signature
and Length of this CD record.


Flags                Lotus
Script Object Flags for Notes/Domino 6. 


Reserved          Reserved
for future use.


 **See Also :**


**[CDLSOBJECT](CDLSOBJECT.md)**


**[CDLSOBJECT\_R6\_TYPE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F777D44B811878D885256A25003F9CAD)**



----------------------------------------------------------------------------------------------------------


 





