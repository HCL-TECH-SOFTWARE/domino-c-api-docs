




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




**Initial Release 5.0.1**



**Data Type : Composite Data; Rich
Text**



**CDFRAMESETHEADER** **-** Preliminary
header information to CDFRAMESET and CDFRAME record(s).


**----------------------------------------------------------------------------------------------------------**



**#include
<fsods.h>**



**Definition :**



typedef struct {


   WSIG  Header;


   WORD  Version;


   WORD  RecCount;   
/\* Total number of CDFRAMESET and CDFRAME


                        
recs that follow \*/


   DWORD Reserved[4];
/\* Reserved for future use, must be 0 \*/


} CDFRAMESETHEADER;


 


**Description :**



Beginning
header record to both a CDFRAMESET and CDFRAME record.


 


Header


Version                   See
FRAMESETHEADER\_VERSION.


RecCount               Total
number of CDFRAMESET and CDFRAME records that follow.


Reserved                Currently
not used, must be 0,


 **See Also :**


**[CDFRAME](CDFRAME.md)**


**[CDFRAMESET](CDFRAMESET.md)**


**[FRAMESETHEADER\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ADDA39C5B801FFB3852569840049A333)**



----------------------------------------------------------------------------------------------------------


 





