




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDIMAGESEGMENT** **-** Structure
which defines an image, such as a GIF or JPEG, segment.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG Header;   /\* Signature and Length \*/  

   WORD DataSize; /\* Actual Size of image bits in bytes, ignoring


                    
any filler \*/  

   WORD SegSize;  /\* Size of segment, is equal to or larger than


                    
DataSize if filler byte added to maintain word


                    
boundary \*/  

} CDIMAGESEGMENT;


 


**Description :**



This
structure defines the image segment data of a JPEG or GIF image and follows a
CDIMAGEHEADER structure.  The number of segments in the image is contained in
the CDIMAGEHEADER and specifies the number of CDIMAGESEGMENT structures to follow. 
An image segment size is 10250 bytes.


 


The fields
in this structure are:


 


Header                   Identifies
this as a CDIMAGESEGMENT record.


DataSize                 Actual
size of image bits in bytes  (10250 per segment).


SeqSize                  10250
bytes or less.


 




----------------------------------------------------------------------------------------------------------


 





