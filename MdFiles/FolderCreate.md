




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



**FolderCreate** **- Creates
new folder.**


**----------------------------------------------------------------------------------------------------------**



**#include <foldman.h>**



STATUS
LNPUBLIC **FolderCreate(**  

      DBHANDLE  hDataDB,  

      DBHANDLE  hFolderDB,  

      NOTEID  FormatNoteID,  

      DBHANDLE  hFormatDB,  

      char far \*pszName,  

      WORD  wNameLen,  

      DESIGN\_TYPE  FolderType,  

      DWORD  dwFlags,  

      NOTEID far \*pNoteID**);**



**Description :**



This
function creates a new folder in the specified database.  If the user does not
have create personal folders access for the database, then an error will be
returned.


 


**Parameters :**



Input :  

hDataDB  -  The handle to the open database where the new folder is to reside. 
This database will also be used to obtain the new folder's design if the
hFormatDB parameter is not specified.  

  

hFolderDB  -  Must be NULLHANDLE.  

  

FormatNoteID  -  Folder/view note with which to base the new folder's design. 
Specify 0L to use the default design.  The default design is specified in an
existing folder's design.  If there is no default design specified in an
existing folder's design, then the default view note is used.  

  

hFormatDB  -  The handle to the open database which contains the folder/view
note with which to base the new folder's design.  You may specify NULLHANDLE if
this is the same as hDataDb.  

  

pszName  -  Name of new folder.  Individual folder names are limited to
DESIGN\_FOLDER\_MAX\_NAME bytes.  If this is to be a cascading folder (subfolder),
use a backslash character to separate the folder names, for example,
"Parent Folder\\New Folder".  In this example, New Folder will be a
subfolder of Parent Folder.  If Parent Folder does not exist, it will be
created.  

  

wNameLen  -  Length of the pszName parameter.  If pszName is NULL terminated,
you may use MAXWORD for this parameter.  

  

FolderType  -  Folder type (DESIGN\_TYPE\_xxx).  Indicates whether folder is to
be shared or private.  

  

dwFlags  -  Reserved for future use.  Specify  0L.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  

pNoteID  -  Pointer to the returned NOTEID of the newly created folder.  

  




 **Sample Usage :**


error = FolderCreate
(hDB2, NULLHANDLE, FormatNoteID, hDB1, 


                         
"API Folder", MAXWORD,  

                          DESIGN\_TYPE\_PRIVATE\_DATABASE,  

                          0L, &FNoteID);


 **See Also :**


**[FolderCopy](FolderCopy.md)**


**[FolderDelete](FolderDelete.md)**


**[FolderDocAdd](FolderDocAdd.md)**


**[FolderDocCount](FolderDocCount.md)**


**[FolderDocRemove](FolderDocRemove.md)**


**[FolderDocRemoveAll](FolderDocRemoveAll.md)**


**[FolderMove](FolderMove.md)**


**[FolderRename](FolderRename.md)**


**[DESIGN\_TYPE\_xxx](DESIGN_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





