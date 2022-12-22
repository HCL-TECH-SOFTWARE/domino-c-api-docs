




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




**Initial Release 5.0**



**Function : Views; Folders**



**NIFFindDesignNoteExt** **- Returns
the note ID of the specified form, view, shared folder, macro, or field note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindDesignNoteExt(**  

      DBHANDLE  hFile,  

      const char far \*Name,  

      WORD  Class,  

      const char \*pszFlagsPattern,  

      NOTEID far \*retNoteID,  

      DWORD  Options**);**



**Description :**



This
function returns the note ID of a form, view, shared folder, macro, or field
note, given the name and NOTE\_CLASS\_xxx.  The name is compared without regard
to case (case insensitive).  

  

Only the following NOTE\_CLASS types are valid for this function:  

NOTE\_CLASS\_FORM  

NOTE\_CLASS\_VIEW  

NOTE\_CLASS\_FILTER  

NOTE\_CLASS\_FIELD  

NOTE\_CLASS\_ALL  

  

Specify NOTE\_CLASS\_VIEW for shared  folders as well as private views.


 


 


This
function uses an on-disk index of these types of notes and is very efficient.


 


The
"pszFlagsPattern" parameter provides a way to extend the
specification of certain NOTE\_CLASS\_xxx types by incorporating Design Flag
Patterns when searching for specific design notes.  Design Flag Pattern
definitions are described in the Tech Note "[Design Flag Patterns](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E9DFB23EF955B6628525672F00051490)".  Tech Notes are
listed in the view, Reference Tools/Tech Notes.


 


**Parameters :**



Input :  

hFile  -  Handle to the database.  

  

Name  -  Pointer to a null-terminated character string that holds the name of
the note you want to find.  

  

Class  -  The type of note which must be one of the following NOTE\_CLASS\_xxx
types:  

NOTE\_CLASS\_FORM  

NOTE\_CLASS\_VIEW  

NOTE\_CLASS\_FILTER  

NOTE\_CLASS\_FIELD  

NOTE\_CLASS\_ALL  

  

If NOTE\_CLASS\_ALL is specified, then the id of the first note found with the
specified name is returned.  The found note will be one of the above
NOTE\_CLASS\_xxx types.  

  

pszFlagsPattern  -  Pointer to a character string defining a Design Flag
Pattern.  See "stdnames.h" for a list of common Design Flag Patterns
(DFLAGPAT\_xxx).  

  

Options  -  Please see FIND\_DESIGN\_NOTE\_xxx for options or zero for no options.  

  




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


**[FIND\_DESIGN\_NOTE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E9DFB23EF955B6628525672F00051490)**


**[NIFCloseCollection](NIFCloseCollection.md)**


**[NIFFindDesignNote](NIFFindDesignNote.md)**


**[NIFFindView](NIFFindView.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





