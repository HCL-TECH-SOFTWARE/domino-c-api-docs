




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



**HTMLAPI\_URLComponent** **-** HTMLAPI\_URLComponent


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef
union


{


            HTMLAPI\_URLTargetComponent          Target;


            HTMLAPI\_URLArg                    Arg;


}
HTMLAPI\_URLComponent;


 


 


**Description :**



To simplify
memory management, the target components and args are unioned in one structure
that can serve as the allocation unit for sequences (arrays) of target
components and args.


 


 


 **Sample Usage :**


see sample html/convpic


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_URLArg](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/5DAF84E33D4E40D1482571960041B509)**


**[HTMLAPI\_URLTargetComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/2827D557FD70E40E48257196003EC7DC)**



----------------------------------------------------------------------------------------------------------


 





