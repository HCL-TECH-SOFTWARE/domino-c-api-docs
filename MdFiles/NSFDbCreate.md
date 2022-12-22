




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



**NSFDbCreate** **- Creates a
new Domino database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCreate(**  

      const char far \*PathName,  

      USHORT  DbClass,  

      BOOL  ForceCreation**);**



**Description :**



This
function creates a new Domino database.  You also may control whether the call
will overwrite an existing database of the same name and the database class.


 


The newly
created database is completely empty.  It has no title, no access control list,
no icon, no forms, no views, and no documents.  Also, the database is closed. 
After creating a database, you must open it with NSFDbOpen or NSFDbOpenExtended
before you can begin to copy/create the various elements of this new database.


 


**Parameters :**



Input :  

PathName  -  A pointer to the pathname of the database to be created.    

  

If the database will be in the default  data directory, you may omit the
directory specifier. If the database will have the filename extension
".NSF", you may omit the extension.    

  

If you are interested in creating a remote database on a particular Lotus
Domino Server, OSPathNetConstruct will allow you to build a fully qualified
network pathname.    

  

Note:  Your ability to perform this function remotely is subject to the access
rights you have to that server.  Access rights to a server is controlled by the
server's use of Server Access Groups, proper certification in your ID file and
the Restrictions section of the server document in the server's Domino
Directory.   

  

DbClass  -  Specifies the class of the database created.  Almost always
specified as DBCLASS\_NOTEFILE.  See DBCLASS\_xxx for other classes that may be
specified.  

  

ForceCreation  -  Controls whether the call will overwrite an existing database
of the same name.  Set to TRUE to overwrite, set to FALSE not to overwrite.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR - Success.  

ERR\_EXISTS - ForceCreation parameter set to FALSE and file to be created
already exists.  

ERR\_DBCLASS - Invalid database class.  

  

  




 **Sample Usage :**



/\* Create destination
database \*/


  

if (error = NSFDbCreate (output\_path, DBCLASS\_NOTEFILE, FALSE))  

{


     /\* Close
previously opened database \*/  

  NSFDbClose (input\_handle);  

  API\_RETURN (ERR(error));  

}


 **See Also :**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[DBCLASS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B460075BDBF)**



----------------------------------------------------------------------------------------------------------


 





