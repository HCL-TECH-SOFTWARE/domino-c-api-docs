




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




**Initial Release 4.0**



**Data Type : Character Manipulation**



**NLS\_INFO** **-** The data
structure that defines the attributes of a character set.


**----------------------------------------------------------------------------------------------------------**



**#include
<nls.h>**



**Definition :**



typedef void NLS\_INFO;


 


**Description :**



An NLS\_INFO
struct defines the attributes of a character set.  It contains a number of
flags and pointers to various translation tables.  Most of the National
Language Services (NLS) functions take a pointer to an NLS\_INFO struct as one
of their arguments.  You should initialize the NLS\_INFO struct by calling the
function OSGetLMBCSCLS() before calling one of the NLS functions.


  

**Note:** This data structure should be treated as READ-ONLY -- modifying
the data structure could have undesired consequences.


 **See Also :**


**[NLS\_PINFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**



----------------------------------------------------------------------------------------------------------


 





