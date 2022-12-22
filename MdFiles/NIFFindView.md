




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




 


**Function : Views; Folders**



**NIFFindView** **- Returns
the note ID of the specified view or shared folder note, given the name.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindView(**  

      DBHANDLE  hFile,  

      const char far \*Name,  

      NOTEID far \*retNoteID**);**



**Description :**



This is a
macro used to return the note ID of a view or shared folder note, given the
name.  The name is compared without regard to case (case insensitive).  

  

This function uses an on-disk index of these types of notes and is very
efficient.  

  

#define
NIFFindView(hFile,Name,retNoteID)
NIFFindDesignNoteExt(hFile,Name,NOTE\_CLASS\_VIEW, DFLAGPAT\_VIEWS\_AND\_FOLDERS,
retNoteID, 0)


 


**Parameters :**



Input :  

hFile  -   Handle to the database.  

  

Name  -   Pointer to a null-terminated character string that holds the name of
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


**[NIFCloseCollection](NIFCloseCollection.md)**


**[NIFFindDesignNote](NIFFindDesignNote.md)**


**[NIFFindDesignNoteExt](NIFFindDesignNoteExt.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**



----------------------------------------------------------------------------------------------------------


 





