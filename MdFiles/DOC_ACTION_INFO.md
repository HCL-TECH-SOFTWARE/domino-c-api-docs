




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



**DOC\_ACTION\_INFO** **-** Data
structure used to pass document action information via Notes/FX.


**----------------------------------------------------------------------------------------------------------**



**#include
<olenotes.h>**



**Definition :**



typedef struct {  

   int  ActionID;  /\* Notes magic cookie identifying this action \*/  

   WORD NameLength;/\* Length of action name string \*/  

   char Name[ACTION\_NAME\_SIZE]; /\* Action name in LMBCS charset \*/  

   DWORD Flags;    /\* ACTION\_FLAG\_xxx \*/  

} DOC\_ACTION\_INFO;


 


**Description :**



This is the
structure of the Notes Document Actions passed through the hDocActions handle
in the NOTES\_DOC\_INFO\_MSG to those OLE objects registered as supporting the
NotesDocAction SetData() format.   It is an array of the following data
structure, whose count is provided in the cNumDocActions member of the
NOTES\_DOC\_INFO\_MSG. This data block must be deallocated by the OLE server. 


 


Notes
provides the OLE server application with an arbitrary number which is used to
identify the action to Notes.  This is referred to internally as a "magic
cookie";  it is similar in use to a handle.  Notes also supplies a
character string with the name of the action;  this string is specified in the
form definition.


 


The fields
in this structure are:


 


ActionID -
Action ID number used by the OLE server application to identify the desired
action to Notes.


 


NameLength -
Number of bytes in the action name string.


 


Name -
Character array containing the action name string.


 


Flags -
Control flags for this action;  for the supported flags, see the entry for
ACTION\_FLAG\_xxx.


 


 **See Also :**


**[NSFDbReopen](NSFDbReopen.md)**


**[NOTES\_DOC\_INFO\_MSG](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CD436B32BF89249C482573FB00322DA3)**


**[ACTION\_FLAG\_xxx](ACTION_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





