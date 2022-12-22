




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



**Data Type : Rich Text; Composite
Data**



**CDFILESEGMENT** **-** Structure
which defines a CSS segment.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    LSIG    Header;        /\* Signature and Length \*/  

    WORD    DataSize;              /\* Actual Size of image bits in bytes,
ignoring any filler \*/  

    WORD    SegSize;               /\*  Size of segment, is equal to or larger
than DataSize   

                                      if filler byte added to maintain word
boundary \*/          

    DWORD   Flags;         /\* currently unused, but someday someone will be
happy this is here \*/  

    DWORD   Reserved;              /\* Reserved for future use \*/  

    /\* File bits for this segment \*/  

} CDFILESEGMENT;


 


 


**Description :**



This
structure defines the file segment data of a Cascading Style Sheet (CSS) and
follows a CDFILEHEADER structure.  The number of segments in the file is
specified in the CDFILEHEADER record.


 


The fields
in this structure are:  

  




Header -
Defines this composite data item as a CDFILESEGMENT item.


  

DataSize - Size of CSS in bytes


  

SegSize - Size of segment. This is equal to or larger than DataSize if a filler
byte is added to maintain the word boundary.


  

Flags - Flags (currently unused)


   

Reserved - Reserved for future use


 


File bits
for this segment (the CSS and the optional filler byte) follow this record.


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note. 


 **See Also :**


**[CDFILEHEADER](CDFILEHEADER.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





