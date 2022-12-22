




<!--
 /\* Font Definitions \*/
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




**Initial Release 8.0.1**



**Data Type : nao**



**NAO\_ENTRY\_INFO** **-** Entry
infomation structure


**----------------------------------------------------------------------------------------------------------**



**#include
<addinout.h>**



**Definition :**



typedef
struct


{


               DWORD                                             dwSize;                                                              /\*
Size of this structure \*/


               NAO\_ENTRY\_DATA                                        EntryData;                                                          /\*
NAO\_ENTRY\_DATA \*/


               NAO\_ENTRY\_RESOURCE                             EntryResource;                                                  /\*
NAO\_ENTRY\_RESOURCE \*/


               WORD                                                wEntryResourceType;                                       /\*
NAO\_RESOURCE\_XXX \*/


               NAO\_IMAGE\_DATA                                         ImageData;                                                        /\*
NAO\_IMAGE\_DATA \*/


               DWORD                                             dwReserved1;                                                    /\*
Reserved \*/


               DWORD                                             dwReserved2;                                                    /\*
Reserved \*/


}
NAO\_ENTRY\_INFO;


 


**Description :**



Entry
infomation structure.


 




----------------------------------------------------------------------------------------------------------


 





