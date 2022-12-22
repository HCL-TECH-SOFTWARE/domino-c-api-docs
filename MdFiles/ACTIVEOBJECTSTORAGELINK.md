




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



**Data Type : Rich Text**



**ACTIVEOBJECTSTORAGELINK** **-** Active
object storage specification.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WORD  Length;   /\* Length of the attachment name following \*/  

   WORD  LinkType; /\* Currently not used \*/  

   DWORD Reserved;  

/\* Variable length string follows (not null terminated).  This


   string is the name
of an attachment which contains data (e.g.,


   a .class file) used
by the active object. \*/  

} ACTIVEOBJECTSTORAGELINK;


 


**Description :**



Java code
used for active object hotspots is stored in $FILE items.  The file name for
the $FILE item containing a class file is specified in this record.  This
record only appears following an ACTIVEOBJECT record, and is part of a CDHOTSPOTBEGIN
record.  The fields of an ACTIVEOBJECTSTORAGELINK record are:


 


Length              Length
of the file attachment name.


LinkType          Reserved; 
must be 0.


Reserved          Reserved; 
must be 0.


 


This record
is followed by the name of the $FILE attachment, in LMBCS format with no NULL
delimiter.


 **See Also :**


**[ACTIVEOBJECT](ACTIVEOBJECT.md)**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





