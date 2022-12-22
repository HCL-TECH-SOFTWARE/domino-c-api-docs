




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



**CDIMAGEHEADER** **-** Structure
which defines an image,such as a GIF or JPEG, header.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   LSIG  Header;       
/\* Signature and Length \*/


   WORD  ImageType;    
/\* Type of image (e.g., GIF, JPEG) \*/


   WORD  Width;        
/\* Width of the image (in pixels) \*/


   WORD  Height;       
/\* Height of the image (in pixels) \*/


   DWORD ImageDataSize;
/\* Size (in bytes) of the image data \*/


   DWORD SegCount;     
/\* Number of CDIMAGESEGMENT records


                          
expected to follow \*/


   DWORD Flags;        
/\* Flags (currently unused) \*/


   DWORD Reserved;     
/\* Reserved for future use \*/


} CDIMAGEHEADER;


 


**Description :**



This
structure is used to define a JPEG or GIF Image that is part of a Domino
document.  The CDIMAGEHEADER structure follows a CDGRAPHIC structure. 
CDIMAGESEGMENT structure(s) then follow the CDIMAGEHEADER.


 


The fields
in this structure are:


 


Header                   Identifies
this as a CDIMAGEHEADER record (SIG\_CD\_IMAGEHEADER).


ImageType             Type
of Image (see CDIMAGETYPE\_xxx)


Width                    Width
of image.


Height                    Height
of image.


ImageDataSize       the
file length of the image.


SegCount               the
number of segments in this image (filelength of image / 10250 (segment size)).


Flags                      Image
flag values (currently unused).


Reserved                unused.


 **See Also :**


**[CDGRAPHIC](CDGRAPHIC.md)**


**[CDIMAGESEGMENT](CDIMAGESEGMENT.md)**


**[CDIMAGETYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/993E6C0FA13C28DA852566280040E817)**



----------------------------------------------------------------------------------------------------------


 





