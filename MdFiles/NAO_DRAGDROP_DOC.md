




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



**NAO\_DRAGDROP\_DOC** **-** Drag/drop
doc structure


**----------------------------------------------------------------------------------------------------------**



**#include
<addinout.h>**



**Definition :**



typedef
struct


{


               DWORD                                             dwSize;                                                              /\*
Size of this structure \*/


               BOOL                                                  bMove;                                                               /\*
TRUE if MOVE, FALSE if COPY \*/


               DWORD                                             dwCount;                                                            /\*
Number of documents being dropped \*/


               DBHANDLE                                        hSourceDb;                                                        /\*
Source database handle for these notes \*/


               HANDLE                                                            hIDTable;                                                           /\*
ID table of documents to drop into folder \*/


               DBHANDLE                                        hDestDb;                                                            /\*
Destination database handle for these notes \*/


               NAO\_SELECT\_INFO                                       DestFolderInfo;                                                  /\*
NAO\_SELECT\_INFO of destination folder \*/


               BOOL                                                  bNamedFolder;                                                  /\*
TRUE if destination folder has a named folder element \*/


               BOOL                                                  bActionEntry;                                                     /\*
TRUE if destination folder has a action element \*/


               DWORD                                             dwReserved1;                                                    /\*
Reserved \*/


               DWORD                                             dwReserved2;                                                    /\*
Reserved \*/


}
NAO\_DRAGDROP\_DOC;


 


**Description :**



Drag/drop
doc structure.


 




----------------------------------------------------------------------------------------------------------


 





