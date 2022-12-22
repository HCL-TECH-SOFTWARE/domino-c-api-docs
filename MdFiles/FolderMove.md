




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



**FolderMove** **- Moves a
folder under another folder.**


**----------------------------------------------------------------------------------------------------------**



**#include <foldman.h>**



STATUS
LNPUBLIC **FolderMove(**  

      DBHANDLE  hDataDB,  

      DBHANDLE  hFolderDB,  

      NOTEID  FolderNoteID,  

      DBHANDLE  hParentDB,  

      NOTEID  ParentNoteID,  

      DWORD  dwFlags**);**



**Description :**



This
function moves the specified folder under a given parent folder.  If the parent
folder is a shared folder, then the child folder must be a shared folder.  If
the parent folder is a private folder, then the child folder must be a private
folder.


 


**Parameters :**



Input :  

hDataDB  -  The handle to the open database where the folder to be moved
resides.  

  

hFolderDB  -  Must be NULLHANDLE.  

  

FolderNoteID  -  NOTEID of folder to be moved.  

  

hParentDB  -  Must be NULLHANDLE.  The parent database will be the same as the
child database.  

  

ParentNoteID  -  NOTEID of the parent folder.  

  

dwFlags  -   Reserved for future use.  Specify  0L.  

  




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


**[FolderDocRemove](FolderDocRemove.md)**


**[FolderDocRemoveAll](FolderDocRemoveAll.md)**


**[FolderRename](FolderRename.md)**



----------------------------------------------------------------------------------------------------------


 





