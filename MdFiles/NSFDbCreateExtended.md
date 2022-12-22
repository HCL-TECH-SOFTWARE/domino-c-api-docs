




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



**Function : Database**



**NSFDbCreateExtended** **- Creates a
new Domino database with additional options.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCreateExtended(**  

      const char far \*PathName,  

      WORD  DbClass,  

      BOOL  ForceCreation,  

      WORD  Options,  

      BYTE  EncryptStrength,  

      DWORD  MaxFileSize**);**



**Description :**



This
function creates a new Domino database.  It provides added functionality to
NSFDbCreate.


 


After
creating a database, you must open it with NSFDbOpen or NSFDbOpenExtended
before you can use it.


 


**Parameters :**



Input :  

PathName  -  A pointer to the pathname of the database to be created.    

  

If the database will be in the default  data directory, you may omit the
directory specifier.  If the database will have the filename extension
".NSF", you may omit the extension.    

  

If you are interested in creating a remote database on a particular Lotus
Domino Server, use OSPathNetConstruct to build a fully qualified network
pathname.    

  

Note:  Your ability to perform this function remotely can also be affected by a
server's use of Server Access Groups and/or your lack of a common certificate. 
If your local user name appears in the target server's notes.ini in a
DENY\_ACCESS= statement, you will not be allowed to create anything on that
server.  If you do not share a common certificate, you will not be allowed to
create anything on that server.  

  

DbClass  -  Specifies the class of the database created.  See DB\_CLASS for
classes that may be specified.  

  

ForceCreation  -  Controls whether the call will overwrite an existing database
of the same name.  Set to TRUE to overwrite, set to FALSE not to overwrite.  

  

Options  -  Database creation option flags.  See DBCREATE\_xxx  

  

EncryptStrength  -  Local encryption level for the database.  See
DBCREATE\_ENCRYPT\_xxx.  Specify DBCREATE\_LOCALSECURITY in order to create a
locally encrypted database.  Otherwise, use DBCREATE\_ENCRYPT\_NONE for this
parameter.  

  

MaxFileSize  -  Optional.  Maximum file size of the database, in bytes.  In
order to specify a maximum file size, use the database class,
DBCLASS\_BY\_EXTENSION and use the option, DBCREATE\_MAX\_SPECIFIED.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR  

ERR\_EXISTS - Database file already exists and the call specified not to
overwrite an existing database.  

ERR\_DBCLASS - Invalid database class.  

ERR\_xxx - Errors returned by lower level functions.   Use OSLoadString to
display/log a description of the error.  

  

  




 **See Also :**


**[NSFDbCreate](NSFDbCreate.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[DBCLASS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B460075BDBF)**


**[DBCREATE\_ENCRYPT\_xxx](DBCREATE_ENCRYPT_xxx.md)**


**[DBCREATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F0BF86FF26183125852562A700582643)**



----------------------------------------------------------------------------------------------------------


 





