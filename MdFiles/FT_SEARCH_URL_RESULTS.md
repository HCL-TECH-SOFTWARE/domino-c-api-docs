




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



**Data Type : Full Text Search**



**FT\_SEARCH\_URL\_RESULTS** **-** FTSearchExtSearch
Results Header when FT\_RESULTS\_URL is set


**----------------------------------------------------------------------------------------------------------**



**#include
<ft.h>**



**Definition :**



typedef struct {  

   DWORD HitCount;  /\* Number of search hits (not necessarily


                      
number returned) \*/  

   WORD  VarLength; /\* Length of variable length strings;


                      
currently unused. \*/


}
FT\_SEARCH\_URL\_RESULTS;


 


**Description :**



Appears
after FT\_SEARCH\_RESULTS when FT\_RESULTS\_URL is set and contains additional
information from extended, multi-database searches.


 




----------------------------------------------------------------------------------------------------------


 





