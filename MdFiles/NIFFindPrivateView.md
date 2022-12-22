




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



**Function : Folders; Views**



**NIFFindPrivateView** **- Returns
the note ID of the specified private view or folder**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindPrivateView(**  

      DBHANDLE  hFile,  

      char far \*Name,  

      NOTEID far \*retNoteID**);**



**Description :**



Given the
name of a private view or folder, this function returns the note ID.   The name
is compared without regard to case (case insensitive).


  

This function uses an on-disk index of these types of notes and is very
efficient.


 


Private
folders that are stored in the user's desktop file, rather than in the
database, cannot be accessed by the C API.  Also, the C API cannot store
private folders in the user's desktop file.  Private folders are stored in the
user's desktop file only by the Notes user interface and only if the user does
not have the access right to create private folders in the database.


 


Note: This
function is implemented as a macro:  

  

#define
NIFFindPrivateView(hFile,Name,retNoteID)
NIFFindPrivateDesignNote(hFile,Name,NOTE\_CLASS\_VIEW,retNoteID)


 


**Parameters :**



Input :  

hFile  -  Handle to the database.  

  

Name  -  Pointer to a null-terminated character string that holds the name of
the note you want to find.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_NOT\_FOUND  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retNoteID  -  Pointer to the returned NOTEID.  

  




 **See Also :**


**[NIFFindDesignNote](NIFFindDesignNote.md)**


**[NIFFindDesignNoteByName](NIFFindDesignNoteByName.md)**


**[NIFFindPrivateDesignNote](NIFFindPrivateDesignNote.md)**


**[NIFFindView](NIFFindView.md)**



----------------------------------------------------------------------------------------------------------


 





