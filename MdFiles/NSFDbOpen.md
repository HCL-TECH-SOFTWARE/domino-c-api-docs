




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




 


**Function : Database**



**NSFDbOpen** **- Opens an
existing Domino database or database template or a directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbOpen(**  

      const char far \*PathName,  

      DBHANDLE far \*rethDB**);**



**Description :**



This
function takes a pathname to an existing Domino database or database template
(whether on a Lotus Domino Server or a local database), opens the database, and
returns a handle to it. All subsequent access to the database is carried out
via this handle.  Use NSFDbClose to close the database file handle and
deallocate the memory associated with it.  

  

This function can also be used to open a directory. The resulting handle can be
passed to NSFSearch to find the contents of the directory.  To open the local
data directory, use OSGetEnvironmentString with the VariableName set to
"Directory" to get the pathname of the local data directory  or if
NULL is specified, the local data directory (the value of the
"Directory=" environment variable from notes.ini) will be opened.    

  

Because this function can open a directory or a database, do not use NSFDbOpen
to test for the existence of a database. To test a handle to distinguish a
database handle from a directory handle, use NSFDbModeGet. NSFDbModeGet takes a
DBHANDLE as input and returns a pointer to a USHORT that specifies whether the
handle is associated with a database or with a directory.  The USHORT values
are defined in DB\_xxx (NSFDbModeGet). 


 


**Parameters :**



Input :  

PathName  -  A pointer to the pathname of a Domino database or a directory. The
string must be null-terminated.  

  

For a database: The directory part of the path may be omitted if the database
is in the data directory.  The filename extension may be omitted if it is
".NSF" but NOT if it is a ".NTF" database template file
extension.  If the database is on a remote server, a full network pathname must
be built with OSPathNetConstruct.  

  

For a directory: If the directory is local, simply use the pathname of the
directory.   If NULL is specified, the local data directory (the value of the
"Directory=" environment variable from notes.ini) will be opened.  If
the directory is remote, build a network pathname with OSPathNetConstruct.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Database successfully opened.  

  

ERR\_NOT\_NSF - File is not a database.  

  

ERR\_NSF\_VERSION - Invalid NSF version.  

  

ERR\_BSAFE\_USER\_ABORT - User cancelled password dialog box.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

rethDB  -  The address of a DBHANDLE in which a handle to the opened database
or directory is returned.  Use this handle for all subsequent access to the
database or directory.  

  




 **Sample Usage :**


/\* Open it and begin
operations \*/  

if (error\_status = NSFDbOpen(dst\_name, &db\_handle\_dst))  

  goto Exit;  

else  

  cleanup\_state += CLOSE\_DST\_DB;


 **See Also :**


**[NSFDbClose](NSFDbClose.md)**


**[NSFDbCreate](NSFDbCreate.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[NSFDbOpenTemplate](NSFDbOpenTemplate.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[OSPathNetParse](OSPathNetParse.md)**



----------------------------------------------------------------------------------------------------------


 





