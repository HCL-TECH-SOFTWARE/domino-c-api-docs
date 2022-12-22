




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




**Initial Release 7.0.2**



**Data Type : HTML**



**URT** **-** URL
Reference Type


**----------------------------------------------------------------------------------------------------------**



**#include
<urltypes.h>**



**Definition :**



typedef enum
\_URT       /\* Reference types \*/


{


   
URT\_None                = 0,


   
URT\_Name                = 1,


   
URT\_Unid                = 2,


   
URT\_NoteId              = 3,


   
URT\_Special             = 4,    /\* special name \*/


   
URT\_RepId               = 5,


/\* SDK END
\*/


                       
/\* <= add new types above here 


                               
do not reuse numbers, do not rely on "URT\_NumberOfTypes"


                               
being the same on each side of the API \*/


/\* SDK
BEGIN \*/


   
URT\_NumberOfTypes           /\* must be the last one \*/


} URT;


 


 


**Description :**



This enumerates ways a
Notes Object can be references in a URL path.


 **Sample Usage :**


see sample
html/convattach


 **See Also :**


**[HTMLAPI\_URLTargetComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/2827D557FD70E40E48257196003EC7DC)**



----------------------------------------------------------------------------------------------------------


 





