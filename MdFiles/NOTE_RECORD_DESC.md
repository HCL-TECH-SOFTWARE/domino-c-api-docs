




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



**Data Type : Note**



**NOTE\_RECORD\_DESC** **-** Note record
descriptor


**----------------------------------------------------------------------------------------------------------**



**#include
<addinout.h>**



**Definition :**



typedef
struct {


               DWORD
dwRecordType;                                 /\* ODS type of extension
record              \*/


               DWORD
dwRecordUsage;                               /\* Unique ID to identify purpose
of record   \*/


               DWORD
dwTotalExtenSize;                                            /\* Size of
extension record + variable data  \*/


               DWORD
dwFlags;                                                            /\* Flags,
undefined bits MBZ. Defined below. \*/


}
NOTE\_RECORD\_DESC;


 


**Description :**



Note record
descriptor: Used to describe another record, called the target record.  This
record can be used to make ODS data extensible. The initial use is to allow for
current and future extensions to the NOTE\_SEAL2\_HDR and NOTE\_SEAL2 records. 


 




----------------------------------------------------------------------------------------------------------


 





