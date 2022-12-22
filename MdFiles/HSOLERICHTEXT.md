




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



**HSOLERICHTEXT** **-** OLE rich
text hotspot record.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;       /\* Signature and length of this record \*/  

   DWORD Flags;        /\* OLERT\_FLAG\_xxx flags \*/  

   WORD  cFileObjName; /\* Length of extendable $FILE object name


                         
which contains object data \*/  

   WORD  Reserved1;    /\* Unused, must be 0 \*/  

   WORD  Reserved2;    /\* Unused, must be 0 \*/  

   WORD  Reserved3;    /\* Unused, must be 0 \*/  

   DWORD Reserved4;    /\* Unused, must be 0 \*/  

/\* The variable length portions go here in the following order:  

         FileObjectName  

\*/  

} HSOLERICHTEXT;


 


**Description :**



This record
contains the name of the OLE object for this rich text hotspot.  This record is
stored following the CDHOTSPOTBEGIN record for hotspots of type
HOTSPOTREC\_TYPE\_OLERICHTEXT.  The length of this record is included in the
length field of the CDHOTSPOTBEGIN record.  The fields in this record are:


 


Header             Contains
the record length; the signature byte is unused.


Flags                Flags
for this record;  see OLERT\_FLAG\_xxx for flag values.


cFileObjName   Length,
in bytes, of the file object name.


Reserved1        Reserved; 
must be 0.


Reserved2        Reserved; 
must be 0.


Reserved3        Reserved; 
must be 0.


Reserved4        Reserved; 
must be 0.


 


This record
is followed by the file object name string.


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**


**[OLERT\_FLAG\_xxx](OLERT_FLAG_xxx.md)**


**[CDOLEOBJ\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B21DB118D79474488525667A0076EC43)**



----------------------------------------------------------------------------------------------------------


 





