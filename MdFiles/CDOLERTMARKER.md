




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




**Initial Release 4.6**



**Data Type : Composite Data; Rich
Text**



**CDOLERTMARKER** **-** OLE update
version marker.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header; /\* Signature and length of this record \*/  

   DWORD Flags;  /\* (reserved) \*/  

} CDOLERTMARKER;


 


**Description :**



This record
is simply a marker in an OLE rich text hot spot that indicates that an OLE
object with an associated rich text field (a $OLEObjRichTextField item) was
updated by Release 4.6 or later of Domino or Notes.  If the OLE object is
opened by an earlier release of Domino or Notes, this record will be ignored
(like any other unrecognized CD record).  If this OLE object is updated from
the rich text field by a release of Domino or Notes prior to 4.6, this record
will not appear.


 


If this
record is present and the OLE object is updated from the rich text field by
Release 4.6 or later of Domino or Notes, the object will not be updated if the
rich text field is older than the contents of the OLE object.  If the rich text
field is newer, the object is updated and a CDOLERTMARKER record is written.


 


The fields
in this record are:


 


Header             Identifies
this as a CDOLERTMARKER record.


Flags                Reserved; 
must be 0.


 


 




----------------------------------------------------------------------------------------------------------


 





