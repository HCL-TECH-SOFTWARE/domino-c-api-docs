




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




**Initial Release 6**



**Data Type : Composite Data**



**CDTEXTPROPERTIESTABLE** **-** Text
Properties Table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct {  

      WSIG   Header;  

      WORD NumberOfEntries;  

} CDTEXTPROPERTIESTABLE;


 


**Description :**




A
field or a run of rich text may contain language information. This language
information is stored in a $TEXTPROPERTIES item. The start or end of a span of
language information is indicated by a CDSPANRECORD structure. The
$TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form
note and/or a document.


 


A
$TEXTPROPERTIES item (also known as a text properties table) is an item of
TYPE\_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by
a CDTEXTPROPERTY structure for each language present. 


 


The
fields in this record are:  

  




Header
-                    Signature and Length of this CD record.


NumberOfEntries
- Number of CDTEXTPROPERTY records to follow. 


 **See Also :**


**[CDSPANRECORD](CDSPANRECORD.md)**


**[CDTEXTPROPERTY](CDTEXTPROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





