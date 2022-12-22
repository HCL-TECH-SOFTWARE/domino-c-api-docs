




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



**Function : Folders**



**FolderCopy** **- Copies a
folder.**


**----------------------------------------------------------------------------------------------------------**



**#include <foldman.h>**



STATUS
LNPUBLIC **FolderCopy(**  

      DBHANDLE  hDataDB,  

      DBHANDLE  hFolderDB,  

      NOTEID  FolderNoteID,  

      char far \*pszName,  

      WORD  wNameLen,  

      DWORD  dwFlags,  

      NOTEID far \*pNewNoteID**);**



**Description :**



This
function creates a new folder and copies the contents of the source folder to
it.  Any subfolders are also copied.


 


**Parameters :**



Input :  

hDataDB  -  The handle to the open database where the source folder resides and
where the new copy of the folder will reside.    

  

hFolderDB  -  Must be NULLHANDLE  

  

FolderNoteID  -  NOTEID of source folder.  

  

pszName  -  Name for the new copy of the folder.  Individual folder names are
limited to DESIGN\_FOLDER\_MAX\_NAME bytes.  If this is to be a cascading folder
(a subfolder), use a backslash character to separate the folder names, for
example, "Parent Folder\\New Copy"  In this example, New Copy will be
a subfolder of Parent Folder.  If Parent Folder does not exist, it will be
created.  

  

wNameLen  -  Length of the pszName parameter.  If pszName is NULL terminated,
you may use MAXWORD for this parameter.  

  

dwFlags  -  Reserved for future use.  Specify  0L.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  

pNewNoteID  -  Pointer to the returned NOTEID of the new copy of the folder. 
You may use NULL for this parameter if you do not require this information.  If
the source folder contains subfolders, the NOTEID returned is the last
subfolder that is copied.  

  




 **Sample Usage :**


error = FolderCopy
(hDB, NULLHANDLE, FolderNoteID, "New Folder", MAXWORD, 0L,
pNewNoteID);


 **See Also :**


**[FolderCreate](FolderCreate.md)**


**[FolderDelete](FolderDelete.md)**


**[FolderDocAdd](FolderDocAdd.md)**


**[FolderDocCount](FolderDocCount.md)**


**[FolderDocRemove](FolderDocRemove.md)**


**[FolderDocRemoveAll](FolderDocRemoveAll.md)**


**[FolderMove](FolderMove.md)**


**[FolderRename](FolderRename.md)**



----------------------------------------------------------------------------------------------------------


 





