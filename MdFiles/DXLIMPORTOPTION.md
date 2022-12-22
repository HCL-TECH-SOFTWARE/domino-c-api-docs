




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




**Initial Release 6**



**Data Type : XML**



**DXLIMPORTOPTION** **-** DXL importer
options for ACL, design elements, and documents


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


        DXLIMPORTOPTION\_IGNORE=1,                    /\*
ignore imported data \*/


        DXLIMPORTOPTION\_CREATE=2,                    /\*
create new data from imported data \*/


        DXLIMPORTOPTION\_IGNORE\_ELSE\_CREATE=3, /\*
if imported data matches existing data, ignore the imported data, \*/


                                                     /\*
... otherwise create it \*/


        DXLIMPORTOPTION\_CREATE\_RESERVED2=4,   /\*
do not used - reserved for future variation of create option \*/


 


        DXLIMPORTOPTION\_REPLACE\_ELSE\_IGNORE=5,       /\*
if imported data matches existing data, then replace existing \*/


                                                     /\*
... data with imported data, else ignore imported data. \*/


        DXLIMPORTOPTION\_REPLACE\_ELSE\_CREATE=6,       /\*
if imported data matches existing data, then replace existing \*/


                                                     /\*
... data with imported data, else create new data from imported data \*/


        DXLIMPORTOPTION\_REPLACE\_RESERVED1=7,  /\*
do not used - reserved for future variation of replace option \*/


        DXLIMPORTOPTION\_REPLACE\_RESERVED2=8,  /\*
do not used - reserved for future variation of replace option \*/


 


        DXLIMPORTOPTION\_UPDATE\_ELSE\_IGNORE=9, /\*
if imported  data matches existing data, then update existing \*/


                                                     /\*
... data with imported data, else ignore imported data. \*/


        DXLIMPORTOPTION\_UPDATE\_ELSE\_CREATE=10,       /\*
if imported data matches existing data, then update existing \*/


                                                     /\*
... data with imported data, else create new data from 


                                                              
imported data \*/


        DXLIMPORTOPTION\_UPDATE\_RESERVED1=11,  /\*
do not used - reserved for future variation of update option \*/


        DXLIMPORTOPTION\_UPDATE\_RESERVED2=12   /\*
do not used - reserved for future variation of update option \*/


 


}
DXLIMPORTOPTION;


 


 **See Also :**


**[DXLGetImporterProperty](DXLGetImporterProperty.md)**


**[DXLSetImporterProperty](DXLSetImporterProperty.md)**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





