




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



**Data Type : Agents; Composite Data**



**CDACTIONFOLDER** **-** Folder
action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;        /\* flags \*/  

   WORD  wFolderNameLen; /\* length of folder name \*/  

   WORD  wSpare;


           /\*      folder
name follows \*/  

} CDACTIONFOLDER;


 


**Description :**



A
CDACTIONFOLDER record is stored in fields of type TYPE\_ACTION, usually the
action field of an Agent.  The action depends on the signature. 
SIG\_ACTION\_MOVETOFOLDER indicates that the data selected by the agent is to be
placed in the folder and deleted from the original location. 
SIG\_ACTION\_COPYTOFOLDER indicates that a copy of the data selected by the agent
is to be placed in the folder.  SIG\_ACTION\_REMOVEFROMFOLDER indicates that the
data selected by the agent is to be removed from the folder.  The fields in
this structure are:


 


Header                               Defines
this composite data item as a CDACTIONFOLDER item.


dwFlags                 Option
flags (see ACTIONFOLDER\_FLAG\_xxx)


wFolderNameLen    Length
of the folder name


wSpare                               Reserved; 
must be 0.


 


This
structure is followed by a packed string containing the folder name.


 **See Also :**


**[ACTIONFOLDER\_FLAG\_xxx](ACTIONFOLDER_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





