




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




 


**Function : Clusters; Database**



**NSFDbOpenExtended** **- Open
database or database template with additional options.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbOpenExtended(**  

      const char far \*PathName,  

      WORD  Options,  

      DHANDLE  hNames,  

      TIMEDATE far \*ModifiedTime,  

      DBHANDLE far \*rethDB,  

      TIMEDATE far \*retDataModified,  

      TIMEDATE far \*retNonDataModified**);**



**Description :**



This
function opens a Domino database or database template on the local system or on
a remote Lotus Domino Server.  NSFDbOpenExtended allows you to open a Domino
database with a scan lock (Domino-based file "coordination"), open a
local database with a specified UserName (hNames parameter), initiate purge or
fixup operations during the open, and/or conditionally open the database only
if it has changed since a supplied time/date.  

  




       This
function can also be used to open a directory on the local system or on a
remote Lotus Domino Server.  

  

NSFDbOpenExtended will not succeed on a directory when used with certain
DBOPEN\_xxx options.  Refer to DBOPEN\_xxx for details.


 


For Lotus
Domino Server cluster installations, this function can be made to
"failover" to another server in the cluster if the one specified in
PathName is not reachable.  If the DBOPEN\_CLUSTER\_FAILOVER flag is specified
and this function is used to open a database on a clustered Lotus Domino Server
and that server is not currently available, then the open will automatically
"failover" to other servers that are members of the same cluster if
the database to be opened exists on other servers in that cluster.  This
failover process is transparent to the caller.  If the database open does
failover and the caller wishes to determine the server/database that was
actually opened, the caller must use the NSFDbPathGet function.  The caller can
then compare the string in PathName with the string returned by NSFDbPathGet to
determine if database open failover occurred. 


 


If a client
or server is running an extension manager that traps a EM\_NSFDBOPENEXTENDED
hook, and the call to NSFDbOpenExtended has the DBOPEN\_NO\_USERINFO flag set,
when the extension manager calls NSFDbUserNameGet, a NULL user name will be
returned.  However if the server itself is calling NSFDbOpenExtended with this
option set, the server's user name will be returned.  


  

Use NSFDbClose to close the database file handle and deallocate the memory
associated with it.


 


**Parameters :**



Input :  

PathName  -  A pointer to a text buffer containing a Domino database file path
specification.  The string should be null-terminated.  If NULL is specified,
the local data directory (the value of the "Directory=" environment
variable from notes.ini) will be opened.  If the database is on a remote
server, you can build a full network pathname with OSPathNetConstruct.    

  

Options  -  WORD containing DBOPEN\_xxx options.  Options may be OR'ed together
to achieve the desired affect.  

  

hNames  -  May be NULLHANDLE or a HANDLE to a NAMES\_LIST structure that
contains a UserName that is used to open a local database.  This causes the
user's ACL permissions in the database to be enforced.  Please see
NSFBuildNamesList for more information on building a NAMES\_LIST structure.  

  

  

ModifiedTime  -  A pointer to a TIMEDATE structure containing a time/date value
that must be older than the database's data and non-data last modified
time/date values for the database to be successfully opened.  If there is
nothing new in the database since the specified time, an error will be
returned.  This is an efficient way to only open the database if there is
"something new in it" since the last time you checked.  NULL may be
used if you wish this check to be ignored during the open.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - database successfully opened.  

  

ERR\_ALREADY\_LOCKED -  Database is currently being replicated or copied
elsewhere.  

  

ERR\_NOT\_NSF - File is not a database.  

  

ERR\_NSF\_VERSION - Invalid NSF version.  

  

ERR\_NO\_MODIFIED\_NOTES - No documents have been modified since specified time.  

  

ERR\_NOACCESS - You are not authorized to perform that operation.  

  

ERR\_OPEN\_FILE - You are not authorized to access that database.  

  

ERR\_OBJECT\_TRUNCATED - File object is truncated - file may have been damaged.  

  

ERR\_NSF\_CORRUPT2 - Database has been corrupted and can't be repaired; cannot
open.  

  

ERR\_BSAFE\_USER\_ABORT - User cancelled password dialog box.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

rethDB  -  The address of a DBHANDLE in which a handle to the open database
will be returned.  This handle may now be used in all NSF database operations
that require a DBHANDLE.  It has no meaning within the context of your native
operating system's file package.  

  

retDataModified  -  The address of a Domino binary time/date structure in which
the last-modified date of all data notes/documents is returned.  

  

retNonDataModified  -  The address of a Domino binary time/date structure in
which the last-modified date of all non-data notes/documents is returned.  

  




 **Sample Usage :**


  

   /\* Create a skim date and check Last Modified date during open \*/  

  

   OSCurrentTIMEDATE(&open\_skim\_td);  

   if(TimeDateAdjust(&open\_skim\_td, 0, 0, 0, WEEK\_AGO, 0, 0))  

   {  

       printf("\nTimedateAdjust() failed\n");  

       goto Exit;  

   }  

  

   /\* Open source database \*/  

  

   if (error\_status = NSFDbOpenExtended(src\_name,  

                          DBOPEN\_WITH\_SCAN\_LOCK, NULLHANDLE,  

                          &open\_skim\_td, &db\_handle\_src,  

                          &data\_td\_src, &nondata\_td\_src))  

   {  

       if (ERR(error\_status) == ERR\_NO\_MODIFIED\_NOTES)  

       {  

           printf("\nSrc Db: %s has not been modified in a week.\n",  

                  src\_name);  

           if (error\_status = NSFDbOpenExtended(src\_name,  

                          DBOPEN\_WITH\_SCAN\_LOCK, NULLHANDLE,  

                          NULL, &db\_handle\_src,  

                          &data\_td\_src, &nondata\_td\_src))  

              goto Exit;  

  

       }  

       else  

           goto Exit;  

   }  

   cleanup\_state += CLOSE\_SRC\_DB;  

  

  




 **See Also :**


**[DBOPEN\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BB9005257B4)**


**[NSFBuildNamesList](NSFBuildNamesList.md)**


**[NSFDbClose](NSFDbClose.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenTemplateExtended](NSFDbOpenTemplateExtended.md)**


**[NSFDbPathGet](NSFDbPathGet.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[OSPathNetParse](OSPathNetParse.md)**



----------------------------------------------------------------------------------------------------------


 





