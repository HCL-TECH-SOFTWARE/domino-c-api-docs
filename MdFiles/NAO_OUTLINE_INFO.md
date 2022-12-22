




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



**NAO\_OUTLINE\_INFO** **-** Outline
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


               char                                                     szName[DESIGN\_FORM\_MAX];                     /\*
Outline name \*/


               char                                                     szAlias[DESIGN\_FORM\_MAX];                       /\*
Outline alias \*/


               DBHANDLE                                        hDb;                                                                   /\*
Handle to current Db \*/


               BOOL                                                  bExtendOutline;                                                 /\*
Indicates whether or not to extend outline \*/


               DWORD                                             dwReserved1;                                                    /\*
Reserved \*/


               DWORD                                             dwReserved2;                                                    /\*
Reserved \*/


}
NAO\_OUTLINE\_INFO;


 


**Description :**



Outline
infomation structure.


 




----------------------------------------------------------------------------------------------------------


 





