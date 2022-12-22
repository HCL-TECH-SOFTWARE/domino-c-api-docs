




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



**NSFDbLocateByReplicaID** **- Locate a
database by replica ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbLocateByReplicaID(**  

      DBHANDLE  hDB,  

      DBID far \*ReplicaID,  

      char far \*retPathName,  

      WORD  PathMaxLen**);**



**Description :**



This
function takes a database handle (DBHANDLE) to the data directory, or to one of
its subdirectories, and the replica ID of a database.  It returns an expanded
path specification for the replica.  The function searches all subdirectories
of the data directory for the database.  

  

Note: If you are trying to locate a replica on a remote Lotus Domino Server,
obtain the replica ID of the local database replica with NSFDbReplicaInfoGet,
build a fully qualified network pathname to the remote server's data directory
with OSPathNetConstruct, use that path with NSFDbOpen to obtain a handle to the
data directory, and then pass that handle to NSFDbLocateByReplicaID to get the
server's pathname for the replica you want.  The network path to that database
may then be constructed using OSPathNetConstruct.


 


**Parameters :**



Input :  

hDB  -  A handle to a directory.  

  

ReplicaID  -  A pointer to the Replica ID of the database you wish to find in
the directory.  

  

PathMaxLen  -  A WORD containing the length of the buffer minus one (1) for the
NULL terminator.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully got path specifications for database.  

  

ERR\_NOT\_DIRECTORY - Handle provided was not a directory.  

  

  

retPathName  -  The address of a text buffer into which the expanded pathname
for the Domino database Replica is returned.  The pathname is returned as a
null-terminated string.  The buffer should be declared with a length of
MAXPATH.  

  




 **Sample Usage :**


   

        if (error\_status = NSFDbOpen(src\_datadir, &db\_handle\_dir))  

            goto Exit;  

  

        cleanup\_state += CLOSE\_DIR\_DB;  

  

        if (error\_status = NSFDbLocateByReplicaID(db\_handle\_dir,  

                             &replica\_info\_dst.ID, path\_by\_replid,  

                             sizeof(path\_by\_replid)-1))  

        {  

            if(ERR(error\_status) != ERR\_NOEXIST)  

                goto Exit;  

        }  

        else  

        {  

            printf("\nGiven: %s Matched with: %s by Replica ID\n",  

                   dst\_expandedpath, path\_by\_replid);  

            printf("Note- Match path is relative to Notes Data\n");  

            printf("Directory, NOT to the directory supplied.\n");  

        }  

        cleanup\_state -= CLOSE\_DIR\_DB;  

        if (error\_status = NSFDbClose(db\_handle\_dir))  

            goto Exit;  

  

    }


 **See Also :**


**[NSFDbPathGet](NSFDbPathGet.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[OSGetDataDirectory](OSGetDataDirectory.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





