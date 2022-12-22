




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




**Initial Release 4.5**



**Data Type : Composite Data**



**CDSTORAGELINK** **-** Structure
for externally stored objects.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header;  

   WORD StorageType; /\* Type of object (Object, Note, URL, etc.) \*/  

   WORD LoadType;    /\* How to load (deferred, on demand, etc.) \*/  

   WORD Flags;       /\* Currently not used \*/  

   WORD DataLength;  /\* Length of data following \*/  

   WORD Reserved[6]; /\* Currently not used \*/  

/\* Storage data follows... \*/  

} CDSTORAGELINK;


 


**Description :**



This
structure stores information for an externally stored object.


 **See Also :**


**[STORAGE\_LINK\_LOAD\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3155D470E469DA5D8525635E008248B8)**


**[STORAGE\_LINK\_TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/04CF1B5532B2751885256678004C9715)**



----------------------------------------------------------------------------------------------------------


 





