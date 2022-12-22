




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




**Initial Release 7.0**



**Data Type : LotusScript**



**LSCOMPILEERRPROC** **-** Callback
action routine for NSFNoteLSCompileExt.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfnote.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR LSCOMPILEERRPROC)(


        const
LSCOMPILE\_ERR\_INFO\* pInfo,      


        void\*
pCtx);


 


**Description :**



The callback
function is only called if there were any compilation errors. 


 


   pInfo            
- (I) pointer to a LSCOMPILE\_ERR\_INFO structure.


   pCtx            
- (I) pointer to the user-defined data.


 **See Also :**


**[LSCOMPILE\_ERR\_INFO;](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/DA2041A0EDFF851D482570BB0059A6A1)**


**[NSFNoteLSCompileExt](NSFNoteLSCompileExt.md)**



----------------------------------------------------------------------------------------------------------


 





