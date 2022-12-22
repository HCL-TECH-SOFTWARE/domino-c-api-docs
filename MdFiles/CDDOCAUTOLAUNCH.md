




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




**Initial Release 4.1**



**Data Type : Composite Data**



**CDDOCAUTOLAUNCH** **-** Format of an
on-disk autolaunch item.


**----------------------------------------------------------------------------------------------------------**



**#include
<oleods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;           /\* Signature and length of this rec \*/  

   DWORD ObjectType;       /\* Type of object to launch,


                             
see AUTOLAUNCH\_OBJTYPE\_xxx \*/  

   DWORD HideWhenFlags;    /\* see HIDE\_xxx \*/  

   DWORD LaunchWhenFlags;  /\* see LAUNCH\_WHEN\_xxx \*/  

   DWORD OleFlags;         /\* see OLE\_xxx \*/  

   DWORD CopyToFieldFlags; /\* see FIELD\_COPY\_xxx \*/  

   DWORD Spare1;  

   DWORD Spare2;  

   WORD  FieldNameLength;  /\* If named field, field name length \*/  

   OLE\_GUID  OleObjClass;  /\* ClassID GUID of OLE object, if create


                             
new \*/  

/\* Field Name, if used, goes here \*/


} CDDOCAUTOLAUNCH;


 


**Description :**



Structure of
an on-disk autolaunch item.  Most of the information contained in this
structure refers to OLE autolaunching behaviors.


 **See Also :**


**[AUTOLAUNCH\_OBJTYPE\_xxx](AUTOLAUNCH_OBJTYPE_xxx.md)**


**[FIELD\_COPY\_xxx](FIELD_COPY_xxx.md)**


**[HIDE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/528F289613D7500E8525630400642FD6)**


**[LAUNCH\_WHEN\_xxx](LAUNCH_WHEN_xxx.md)**


**[OLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3F1A17AE2D93A6568525630400687B7C)**



----------------------------------------------------------------------------------------------------------


 





