




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



**CDSPANRECORD** **-** Describes
the start or end of a span of language information for a field or a run of rich
text. 


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      BSIG Header;               /\* Signature and length of this record \*/  

      DWORD PropID;           /\* Property Number \*/  

      } CDSPANRECORD;


 


 


**Description :**



 


This
CD Record describes the start or end of a span of language information for a
field or a run of rich text. The fields in this record are:


 


Header
- Signature and Length of this CD record.


PropID
-  Corresponds to the value of the PropID member of a CDTEXTPROPERTY record.


 


A
field or a run of rich text may contain language information. This language
information is stored in a $TEXTPROPERTIES item. The start or end of a span of
language information is indicated by a CDSPANRECORD structure. The $TEXTPROPERTIES
item and the CDSPANRECORD structures may be stored on a form note and/or a
document.


 


A
$TEXTPROPERTIES item (also known as a text properties table) is an item of
TYPE\_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by
a CDTEXTPROPERTY structure for each language present. 


 


A
CDSPANRECORD record with a SIG\_CD\_SPAN\_BEGIN signature is followed by CD
records pertaining to either a field or a run of rich text, and a CDSPANRECORD
record with a SIG\_CD\_SPAN\_END signature.  


 


A
CDTEXTPROPERTIESTABLE NumberOfEntries member reflects the number of
CDTEXTPROPERTY records to follow. Each of these CDTEXTPROPERTY records' PropID
member reflects the position of its language in the text properties table. A
CDSPANRECORD PropID member corresponds to the value of the PropID member of a
CDTEXTPROPERTY record.


 **See Also :**


**[CDTEXTPROPERTIESTABLE](CDTEXTPROPERTIESTABLE.md)**


**[CDTEXTPROPERTY](CDTEXTPROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





