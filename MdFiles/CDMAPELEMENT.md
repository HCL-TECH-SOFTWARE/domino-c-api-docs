




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



**CDMAPELEMENT** **-** Structure
defining a MAP element.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    WSIG  Header;  

   DWORD Flags;               /\* reserved for future use \*/  

   WORD  MapNameLength;       /\* length of map name that follows \*/  

   WORD  LastDefaultRegionID; /\* last number used in auto


                                
generating default region names \*/  

   WORD  LastRectRegionID;    /\* last number used in auto


                                 generating
rect names \*/  

   WORD  LastCircleRegionID;  /\* last number used in auto


                                
generating circle names \*/  

   WORD  LastPolyRegionID;    /\* last number used in auto


                                
generating polygon names \*/  

   BYTE  Reserved[16];  

/\* variable part of map element follows:  

 \*  MapName (string, not  null terminated)  

 \*/  

} CDMAPELEMENT;


 


**Description :**



Part of a
client side image MAP which describes each region in an image and indicates the
location of the document to be retrieved when the defined area is activated..


 


Header       


Flags                                  Reserved
for future use.


MapNameLength                 Map
Name Length.


LastDefaultRegionID           Last
number used in automatically generating default region names.


LastRectRegionID               Last
number used in automatically generating default rectangle names.


LastCircleRegionID             Last
number used in automatically generating circle names.


LastPolyRegionID               Last
number used in automatically generating polygon names.


Reserved[16]


 


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record sturctures such as this when accessing rich text item
data in a note.


 **See Also :**


**[CDAREAELEMENT](CDAREAELEMENT.md)**


**[CDBEGINRECORD](CDBEGINRECORD.md)**


**[CDENDRECORD](CDENDRECORD.md)**


**[CDEVENT](CDEVENT.md)**


**[CDIDNAME](CDIDNAME.md)**


**[CDMAPELEMENT\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7ED455B0B35B74E785256678004D389E)**



----------------------------------------------------------------------------------------------------------


 





