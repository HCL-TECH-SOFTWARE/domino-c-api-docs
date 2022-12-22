




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : Notes/FX data**



**NOTES\_HNOTE\_MSG** **-** Notes/FX
data sent by  OLE server to Notes to update an embedded object.


**----------------------------------------------------------------------------------------------------------**



**#include
<olenotes.h>**



**Definition :**



typedef struct {  

   NOTEHANDLE hNote;     /\* Handle to a copy of the server's updated  

                            hNote \*/  

   DWORD      Unused[3]; /\* Future use \*/  

} NOTES\_HNOTE\_MSG;


 


**Description :**



This is the
structure of the Notes/FX data that an OLE server's GetData method sends to
Notes to update an object embedded in a note. The hNote parameter is the handle
of a copy of the hFXNote that Notes sent to the OLE server application in a
previous NOTES\_DOC\_INFO\_MSG.


 **Sample Usage :**


 


 **See Also :**


**[DOC\_FLAGS\_xxx](DOC_FLAGS_xxx.md)**


**[DOC\_OPENMODE\_xxx](DOC_OPENMODE_xxx.md)**


**[NOTES\_DOC\_INFO\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00330043005400B185255EC60071FB64)**


**[NSFDbReopen](NSFDbReopen.md)**


**[USER\_ACCESS\_xxx](USER_ACCESS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





