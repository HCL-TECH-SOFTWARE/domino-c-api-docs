




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



**Function : Database**



**NSFDbMajorMinorVersionGet** **- Get the
major and minor version numbers for an open database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbMajorMinorVersionGet(**  

      DBHANDLE  hDB,  

      WORD far \*retMajorVersion,  

      WORD far \*retMinorVersion**);**



**Description :**



The
NSFDbMajorMinorVersionGet API routine allows a C API program to obtain the
major and minor version numbers of an open database.  The major version number
indicates which releases of Domino and Notes software are able to access that
database.  The major verson number of a database is the same as the ODS version
number that is displayed in the Notes Client File/Database/Properties/second
information tab.  The minor version number indicates small changes to the
internal format of a database, and is generally of little interest to a C API
program.  Each release of Domino or Notes software can access databases that
have a major version number that is less than or equal to a particular value
associated with that release.  A Domino database that has a major version
number that is greater than the major version number associated with a
particular Domino or Notes release cannot be accessed by that release.  The
following table shows which major version numbers can be accessed by particular
releases of Domino or Notes:  

  

  






|  |  |
| --- | --- |
| Domino or Notes Software Releases | Major Version Numbers That Can Be Accessed |
| 1.x | 16 |
| 2.x | 16 |
| 3.x | 17
 or less |
| 4.0,
 4.1, 4.5x, 4.6.x
5.0 -
 5.0.12, 6 - 6.0.3, 6.5, 7.0
9.0 | 20
 or less
43 or less
52 |


 


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully got major and minor version numbers for this database.  

  

ERR\_FUNC\_NOT\_IMPL -  The requested function is not supported by the software on
this server.  

  

  

retMajorVersion  -  The address of a WORD into which the major version number
of the database is returned.  

  

retMinorVersion  -  The address of a WORD into which the minor version number
of the database is returned.  

  




 **Sample Usage :**


/\* Output major and
minor version numbers \*/  

   

if (rc = NSFDbMajorMinorVersionGet(db\_handle, &major\_ver, &minor\_ver))  

      goto Exit;  

  

printf("\nMajor ver: %d, minor ver: %d\n", major\_ver, minor\_ver);


 **See Also :**


**[NSFDbClose](NSFDbClose.md)**


**[NSFDbGetBuildVersion](NSFDbGetBuildVersion.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





