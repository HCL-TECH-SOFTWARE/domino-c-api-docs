




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



**Xml\_Validation\_Option** **-** Values for
XML validation options.


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


        Xml\_Validate\_Never
= 0,


        Xml\_Validate\_Always
= 1,


        Xml\_Validate\_Auto
= 2


 


}
Xml\_Validation\_Option;


 


**Description :**



These values
can be used to set members within the DXL\_IMPORT\_PROPERTY structure and the
XSLT\_PROPERTY structure.  For the DXL\_IMPORT\_PROPERTY structure the member is
iInputValidationOption and for the XSLT\_PROPERTY structure the member is
xsltInputValidationOption.


 **See Also :**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**


**[XSLT\_PROPERTY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3C3B0B41F7C4835085256C2B004FD179)**



----------------------------------------------------------------------------------------------------------


 





