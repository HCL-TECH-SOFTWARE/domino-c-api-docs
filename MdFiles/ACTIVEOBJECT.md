




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



**ACTIVEOBJECT** **-** Hotspot
active object record.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WORD  Version;          /\* Version number \*/  

   WORD  ObjectType;       /\* Type of active object \*/  

   DWORD Flags;            /\* Flags \*/  

   BYTE  WidthUnitType;    /\* Currently only


                             
ACTIVEOBJECT\_UNIT\_PIXELS and


                             
ACTIVEOBJECT\_UNIT\_PERCENT supported \*/  

   BYTE  HeightUnitType;   /\* Currently only


                             
ACTIVEOBJECT\_UNIT\_PIXELS and


                             
ACTIVEOBJECT\_UNIT\_PERCENT supported \*/  

   DWORD Width;            /\* Width of active object \*/  

   DWORD Height;           /\* Height of active object \*/  

   WORD  SpaceUnitType;    /\* Currently  not used \*/  

   WORD  HSpace;           /\* Currently not used \*/  

   WORD  VSpace;           /\* Currently not used \*/


   WORD 
DocURLNameLength; /\* Length of document URL string that follows \*/  

   WORD  CodebaseLength;  /\* Length of codebase string that follows \*/  

   WORD  CodeLength;              /\* Length of code string that follows \*/  

   WORD  ObjectNameLength; /\* Length of object name string that follows \*/  

   WORD  StorageLinkCount; /\* Number of ACTIVEOBJECTSTORAGELINK


                             
structures that follow \*/   

   WORD  ParamCount;       /\* Number of ACTIVEOBJECTPARAM


                             
structures that follow \*/  

   BYTE  Used[16];  

/\* Variable length data (strings not null-terminated) follows here:  

 - Document URL string  

 - Codebase string  

 - Code string (SRC info for plugins)  

 - Object name (for Java applets)  

 - ACTIVEOBJECTPARAM info (should be ParamCount number of these -


   Plugin ATTRIBUTE
info should be here).  

 - ACTIVEOBJECTSTORAGELINK info (should be StorageLinkCount number  

   of these). \*/  

} ACTIVEOBJECT;


 


**Description :**



This record
contains the active object information for an active object hotspot.  This
record is stored following the CDHOTSPOTBEGIN record for hotspots of type
HOTSPOTREC\_TYPE\_ACTIVEOBJECT.  The length of this record is included in the
length field of the CDHOTSPOTBEGIN record.  The fields in this record are:


 


Version                         Version
number for the ACTIVEOBJECT record;  see ACTIVEOBJECT\_VERSIONxxx.


ObjectType                   Type
of active object;  must be one of ACTIVEOBJECT\_TYPE\_xxx.


Flags                            Flags.


UnitType                      In
Release 4.6, only ACTIVEOBJECT\_UNIT\_PIXELS is supported.


Width                           Width
of the active object.


Height                          Height
of the active object.


SpaceUnitType             Reserved; 
must be 0.


HSpace                        Reserved; 
must be 0.


VSpace                        Reserved; 
must be 0.


DocURLNameLength    Length
of document URL string.


CodebaseLength           Length
of codebase string.


CodeLength                  Length
of code string.


ObjectNameLength       Length
of the object name string.


StorageLinkCount         Number
of ACTIVEOBJECTSTORAGELINK records.


ParamCount                 Number
of ACTIVEOBJECTPARAM records.


Used                            



 


This record
is followed by the string values, in LMBCS format with no NULL delimiter:


 


Document URL
name.


Codebase
string.


Code string
(source information for plugins and Java).


Object name
(for OLE objects).


 


Note that
comments in editods.h indicate that the Object name is for Java applets.  This
is incorrect.  The object name is for OLE objects.


 


The ACTIVEOBJECTSTORAGELINK
and ACTIVEOBJECTPARAM records follow the strings.


 **See Also :**


**[ACTIVEOBJECT\_TYPE\_xxx](ACTIVEOBJECT_TYPE_xxx.md)**


**[ACTIVEOBJECT\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FFD36B0F9E4624DB852564BA0055E8CC)**


**[ACTIVEOBJECT\_UNIT\_xxx](ACTIVEOBJECT_UNIT_xxx.md)**


**[ACTIVEOBJECT\_FLAG\_xxx](ACTIVEOBJECT_FLAG_xxx.md)**


**[ACTIVEOBJECTPARAM](ACTIVEOBJECTPARAM.md)**


**[ACTIVEOBJECTSTORAGELINK](ACTIVEOBJECTSTORAGELINK.md)**



----------------------------------------------------------------------------------------------------------


 





