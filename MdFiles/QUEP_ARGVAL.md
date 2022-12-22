




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
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
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




 


**Symbolic Value :** 



**QUEP\_ARGVAL** **-** Query
Argument Value


**----------------------------------------------------------------------------------------------------------**



**#include <dbmiscods.h>**



 **Sample Usage :**


        typedef struct { 


                              WORD type; /\*
Standard NSF types: TYPE\_TEXT, TYPE\_NUMBER, TYPE\_TIME. \*/ 


                              DWORD length; /\*
For all textual values. \*/ 


                              DWORD ordinal; /\*
The nth argument in the query (so, the list needn't be in order). \*/ 


                              BOOL bBinaryForm;
/\* Whether NUMBER and DATETIME values have been created in the Value area. \*/ 


                              /\* Argument names
can only be 16 bytes long. \*/ 


                              char ArgName[16];



                              char Value[256];
/\* The stringized value. \*/ 


               } QUEP\_ARGVAL


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





