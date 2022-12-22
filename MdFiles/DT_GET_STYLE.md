




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



**Function : Rich Text**



**DT\_GET\_STYLE** **- Retrieves
the style value from DTFlags**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



DWORD **DT\_GET\_STYLE(**  

      DWORD  dwflag**);**



**Description :**



This
function retrieves the style value from DTFlags (see DT\_XXX). 


 


It is
implemented as a macro:


 


#define
DT\_GET\_STYLE(dwflag) ((dwflag & DT\_STYLE\_MSK) >> 0x10)


 


**Parameters :**



Input :  

dwflag  -  DTFlag (see DT\_XXX).  

  




Output :  

(routine)  -  The border type that is set in the DTFlags member of a
CDEXT2FIELD structure.  See the DT\_STYLE values in the DT\_xxx [CDEXT2FIELD -
DTFlags] symbolic for possible values.  

  

  




 **See Also :**


**[CDEXT2FIELD](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6807B7F2AFEC3988482573FB00322DA5)**


**[DT\_xxx [CDEXT2FIELD - DTFlags]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/38F1D1816A01E4D48525672E00802904)**



----------------------------------------------------------------------------------------------------------


 





