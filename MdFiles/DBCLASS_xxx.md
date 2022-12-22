




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Database**



**DBCLASS\_xxx** **-** Classes of
Domino databases.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCLASS\_BY\_EXTENSION             -  The type of the database
is determined by the filename extension. The extensions and their database
classes are .NSX (NSFTESTFILE), .NSF (NOTEFILE), .DSK (DESKTOP), .NCF
(NOTECLIPBOARD), .NTF (TEMPLATEFILE), .NSG (GIANTNOTEFILE), .NSH
(HUGENOTEFILE), NTD (ONEDOCFILE), NS2 (V2NOTEFILE), NTM (ENCAPSMAILFILE).  

  

      DBCLASS\_NSFTESTFILE    -  A test database.  

  

      DBCLASS\_NOTEFILE          -  A standard Domino database.  

  

      DBCLASS\_DESKTOP           -  A Notes desktop (folders, icons, etc.).  

  

      DBCLASS\_NOTECLIPBOARD          -  A Notes clipboard (used for cutting and
pasting).  

  

      DBCLASS\_TEMPLATEFILE   -  A database that contains every type of note
(forms, views, ACL, icon, etc.) except data notes.  

  

      DBCLASS\_GIANTNOTEFILE            -  A standard Domino database, with size
up to 1 GB. This was used in Notes Release 3 when the size of a previous
version of a database had been limited to 200 MB.  

  

      DBCLASS\_HUGENOTEFILE             -  A standard Domino database, with size
up to 1 GB. This was used in Notes Release 3 when the size of a previous
version of a database had been limited to 300 MB.  

  

      DBCLASS\_ONEDOCFILE     -  One document database with size up to 10MB.
Specifically used by alternate mail to create an encapsulated database.
Components of the document are further limited in size. It is not recommended
that you use this database class with NSFDbCreate. If you do, and you get an
error when saving the document, you will need to re-create the database using
DBCLASS\_NOTEFILE.  

  

      DBCLASS\_V2NOTEFILE      -  Database was created as a Notes Release 2
database.  

  

      DBCLASS\_ENCAPSMAILFILE          -  One document database with size up to
5MB. Specifically used by alternate mail to create an encapsulated database.
Components of the document are further limited in size. It is not recommended
that you use this database class with NSFDbCreate. If you do, and you get an
error when saving the document, you will need to re-create the database using
DBCLASS\_NOTEFILE.  

  

      DBCLASS\_LRGENCAPSMAILFILE    -  Specifically used by alternate mail. Not
recomended for use with NSFDbCreate.  

  

      DBCLASS\_V3NOTEFILE      -  Database was created as a Notes Release 3
database.  

  

      DBCLASS\_OBJSTORE         -  Object store.  

  

      DBCLASS\_V3ONEDOCFILE             -  One document database with size up to
10MB. Specifically used by Notes Release 3 alternate mail to create an
encapsulated database. Not recomended for use with NSFDbCreate.  

  

      DBCLASS\_V4NOTEFILE      -  Database was created specifically for Domino
and Notes Release 4.  

  

      DBCLASS\_V5NOTEFILE      -  Database was created specifically for Domino
and Notes Release 5.  

  

      DBCLASS\_V6NOTEFILE      -  Database was created specifically for Domino
and Notes Release Notes/Domino 6.  

  

      DBCLASS\_V8NOTEFILE      -  Database was created specifically for Domino
and Notes Release Notes/Domino 8.  

  

      DBCLASS\_V85NOTEFILE     -  Database was created specifically for Domino
and Notes Release Notes/Domino 8.5.  

  

      DBCLASS\_V9NOTEFILE      -  Database was created specifically for Domino
and Notes Release Notes/Domino 9.  

  

      DBCLASS\_MASK     -  Used to mask out the most significant byte in the
DBCLASS\_xxx value.  

  

      DBCLASS\_VALID\_MASK      -  Used to mask out the least significant byte in
the DBCLASS\_xxx value.  

  




**Description :**



These
symbolic constants define the various classes that can be specified when a
database is created.


 **See Also :**


**[NSFDbCreate](NSFDbCreate.md)**


**[NSFDbClassGet](NSFDbClassGet.md)**



----------------------------------------------------------------------------------------------------------


 





