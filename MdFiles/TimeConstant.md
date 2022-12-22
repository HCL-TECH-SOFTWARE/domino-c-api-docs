




<!--
 /\* Font Definitions \*/
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




 


**Function : Time**



**TimeConstant** **- Sets a
TIMEDATE value to one of a set of known constants.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



void
LNPUBLIC **TimeConstant(**  

      WORD  TimeConstantType,  

      TIMEDATE far \*tdptr**);**



**Description :**



This
function sets a given TIMEDATE value to one of the following constants: 
minimum value, maximum value, or wildcard (ANYDAY/ALLDAY).  See Symbolic Value,
TIMEDATE\_xxx.


 


**Parameters :**



Input :  

TimeConstantType  -  A TIMEDATE constant.  See Symbolic Value, TIMEDATE\_xxx.  

  




Output :  

(routine)  -  None  

  

  

tdptr  -  Pointer to the returned TIMEDATE value.  

  




 **See Also :**


**[TIMEDATE](TIMEDATE.md)**


**[TIMEDATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/001B0059004800E385255E9F005474DC)**



----------------------------------------------------------------------------------------------------------


 





