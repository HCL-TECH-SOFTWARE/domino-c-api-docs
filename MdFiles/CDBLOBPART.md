




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



**CDBLOBPART** **-** Structure
which defines a 'Binary Large Object'


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG Header;   /\*
Signature and length of this record) \*/


   WORD OwnerSig; /\*
Sig of the owner of this data \*/


   WORD Length;   /\*
Length of the data that follows \*/


   WORD BlobMax;  /\*
Block size used by the writer of the blob \*/


   BYTE Reserved[8];


} CDBLOBPART;


 


**Description :**



This CD
record is used in conjunction with CD record CDEVENT.  If a CDEVENT record has
an ActionType of ACTION\_TYPE\_JAVASCRIPT then CDBLOBPART contains the JavaScript
code.  There may be more then one CDBLOBPART record for each CDEVENT. 
Therefore it may be necessary to loop thorough all of the CDBLOBPART records to
read in the complete JavaScript code.


 **See Also :**


**[CDEVENT](CDEVENT.md)**



----------------------------------------------------------------------------------------------------------


 





