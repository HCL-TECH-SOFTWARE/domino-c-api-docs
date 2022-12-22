




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



**NSFDbPathGet** **- Given a
database handle, get the file name string.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbPathGet(**  

      DBHANDLE  hDB,  

      char far \*retCanonicalPathName,  

      char far \*retExpandedPathName**);**



**Description :**



This
function takes a database handle (DBHANDLE) and returns canonical and/or
expanded path specifications.


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully got path specifications for database.  

  

  

retCanonicalPathName  -  The address of a text buffer that in which the canonical
pathname for the Domino database associated with hDB is returned.   The
pathname is returned as a null-terminated LMBCS string.   The buffer should be
declared with a length of MAXPATH.    If NULL is provided, nothing is
returned.    

  

A canonical pathname is a pathname that is relative to the Domino or  Data
Directory, and is not fully qualified (does not have a drive letter, etc).  It
is useful for comparing 2 different database handles to see if they refer to
the same file, since no matter what file name the user provided, the canonical
pathname will always be returned as a relative pathname.  

  

retExpandedPathName  -  The address of a text buffer in which the expanded
pathname for the Domino database associated with hDB is returned.  The pathname
is returned as a null-terminated LMBCS string.  The buffer should be declared
with a length of MAXPATH.  If NULL is provided, nothing is returned.  

  

For a remotely accessed database located on a Lotus Domino Server, the expanded
pathname is the same as the canonical pathname.  If the database is located on
the same machine as the API program, the expanded pathname consists of a
physical or redirected drive letter, all directories required to reach the
Domino database, the filename and the appropriate database class extension
suffixed.  

  




 **Sample Usage :**


   

   /\* Output PATH and ID info on both Dbs \*/  

    

 if (error\_status = NSFDbPathGet(db\_handle\_src,  

                                   src\_canonicalpath,  

                                   src\_expandedpath))  

       goto Exit;  

  

   printf("Canonical Path of SRC   = %s\n", src\_canonicalpath);  

   printf("Expanded Path of SRC        = %s\n", src\_expandedpath);  

  




 **See Also :**


**[NSFDbLocateByReplicaID](NSFDbLocateByReplicaID.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[OSPathNetParse](OSPathNetParse.md)**



----------------------------------------------------------------------------------------------------------


 





