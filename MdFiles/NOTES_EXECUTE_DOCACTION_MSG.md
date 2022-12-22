




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




**Initial Release 4.0**



**Data Type : Notes/FX data**



**NOTES\_EXECUTE\_DOCACTION\_MSG** **-** Used by OLE
server to request Notes to perform an action.


**----------------------------------------------------------------------------------------------------------**



**#include
<olenotes.h>**



**Definition :**



typedef struct {  

   int ActionID;    /\* Doc action ID for Notes to process \*/  

   DWORD Flags;     /\* Reserved;  must be 0 \*/  

   DWORD Unused[3]; /\* Reserved;  must be 0 \*/  

} NOTES\_EXECUTE\_DOCACTION\_MSG;


 


**Description :**



This data
structure is passed by an OLE server to Notes in response to an OLE request for
data in the NotesDocAction format.


 **See Also :**


**[NOTES\_DOC\_INFO\_MSG](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD436B32BF89249C482573FB00322DA3)**


**[DOC\_ACTION\_INFO](DOC_ACTION_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





