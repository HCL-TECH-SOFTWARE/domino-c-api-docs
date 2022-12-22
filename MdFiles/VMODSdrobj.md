




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




**Initial Release 4.0**



**Data Type : Navigators**



**VMODSdrobj** **-** Common
fields in Navigator CD records - "Byte" signature.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   BSIG      Header;  

   VMODSrect ObjRect;  

   WORD      flags;  

   WORD      NameLen;  

   WORD      LabelLen;  

   FONTID    FontID;  

   WORD      TextColor;  

   WORD      Alignment;  

   WORD      bWrap;  

   DWORD     spare[4]; /\* for future use \*/  

} VMODSdrobj;


 


**Description :**



This
structure contains fields common to the composite data records for the graphical
objects in a Navigator.  The fields in this structure are:


 


Header             Signature
identifying the type of Navigator CD record.


ObjRect            Bounding
rectangle for this graphical object.   See VMODSrect.


flags                 Option
flags.   Set to 7.


NameLen          Length
of the name for the graphical object;  may be 0.


LabelLen           Length
of the displayed label of the graphical object;  may be 0.


FontID              Font
ID to use when displaying the label.   See FONTID.


TextColor         Color
to use for the label text.   Use NOTES\_COLOR\_xxx value.


Alignment         Alignment
of the label text.   Set to 0.


bWrap              If
TRUE, apply word-wrap when displaying the label.


spare                Reserved; 
must be 0.


 


The Header
field contains a BYTE length subfield.  Some Navigator CD records use
VMODSbigobj, which contains a WORD length subfield.


 **See Also :**


**[VMODSbigobj](VMODSbigobj.md)**


**[VMODSrect](VMODSrect.md)**


**[VIEWMAP\_RECT\_RECORD](VIEWMAP_RECT_RECORD.md)**


**[VIEWMAP\_BITMAP\_RECORD](VIEWMAP_BITMAP_RECORD.md)**


**[VIEWMAP\_REGION\_RECORD](VIEWMAP_REGION_RECORD.md)**



----------------------------------------------------------------------------------------------------------


 





