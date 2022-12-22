




<!--
 /\* Font Definitions \*/
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



**Function : Folders**



**FolderDocRemove** **- Removes
the specified document(s) from a folder.**


**----------------------------------------------------------------------------------------------------------**



**#include <foldman.h>**



STATUS
LNPUBLIC **FolderDocRemove(**  

      DBHANDLE  hDataDB,  

      DBHANDLE  hFolderDB,  

      NOTEID  FolderNoteID,  

      DHANDLE  hTable,  

      DWORD  dwFlags**);**



**Description :**



This
function removes the document(s) specified in an ID Table from a folder.


 


**Parameters :**



Input :  

hDataDB  -  The handle to the open database where the folder resides.  

  

hFolderDB  -  Must be NULLHANDLE.  

  

FolderNoteID  -  NOTEID of folder containing document(s) to be removed.  

  

hTable  -  Handle to the ID Table of document(s) to be removed.  

  

dwFlags  -  Reserved for future use.  Specify  0L.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  




 **See Also :**


**[FolderCopy](FolderCopy.md)**


**[FolderCreate](FolderCreate.md)**


**[FolderDelete](FolderDelete.md)**


**[FolderDocAdd](FolderDocAdd.md)**


**[FolderDocCount](FolderDocCount.md)**


**[FolderDocRemoveAll](FolderDocRemoveAll.md)**


**[FolderMove](FolderMove.md)**


**[FolderRename](FolderRename.md)**



----------------------------------------------------------------------------------------------------------


 





