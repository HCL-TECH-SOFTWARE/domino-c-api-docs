




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




**Initial Release 5.0.9**



**Function : Database**



**NSFDbGetMajMinVersion** **- Get
information about code level running on a machine**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetMajMinVersion(**  

      DBHANDLE  hDb,  

      BUILDVERSION far \*retBuildVersion**);**



**Description :**



This
function returns a BUILDVERSION structure which contains all types of
information about the level of code running on a machine.  See BUILDVERSION
structure for more information.


 


**Parameters :**



Input :  

hDb  -  A handle to an open Notes database.  If the database is LOCAL, then the
build information returned will be for the LOCAL version of Notes and if the
database is REMOTE, then the build version returned will be for the REMOTE
version of the Notes Server.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully obtained Major/Minor Version.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retBuildVersion  -  The address of a BUILDVERSION structure where information
will be returned.  This structure will be all 0's if the database is remote and
the remote server does not support this function.  

  




 **Sample Usage :**


BUILDVERSION bv;  

  

.  

.  

.  

  

   error = NSFDbOpen(argv[1], &db\_handle);  

   if (!error)  

          {  

          error = NSFDbGetMajMinVersion(db\_handle, &bv);  

          NSFDbClose(db\_handle);  

          if (!error)  

                 {  

                 printf("%d\t%d\t%d\t%d\t%d\t%d\n", bv.MajorVersion,
bv.MinorVersion, bv.QMRNumber, bv.QMUNumber, bv.HotfixNumber, bv.Flags);  

                 }  

          else  

                 {  

                 xprintf("Error getting version!\n");  

                 }  

          }


 **See Also :**


**[BLDVERFLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7737274DF2E422F185256A6800608933)**


**[BUILDVERSION](BUILDVERSION.md)**


**[NSFDbOpen](NSFDbOpen.md)**



----------------------------------------------------------------------------------------------------------


 





