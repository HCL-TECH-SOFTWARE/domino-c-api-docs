




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



**Function : Clusters; Database**



**NSFDbMarkForDelete** **- Marks a
database for deletion when there are no more user sessions attached to the
database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbMarkForDelete(**  

      const char far \*dbPathPtr**);**



**Description :**



The
NFSDbMarkForDelete function marks a cluster database for pending deletion. The
function modifies the database option flags to include
DBOPTION\_MARKED\_FOR\_DELETE and DBOPTION\_OUT\_OF\_SERVICE.   As a result, when a
call to NFSDbMarkForDelete is successful,  the Cluster Manager denies any new
access requests to the database.  After all active users complete their tasks
and close the database, the Cluster Manager pushes changes to a replica and
then deletes the database.   


 


Use
this function with extreme caution. It is impossible to programatically unmark
a database that is marked for deletion by NFSDbMarkForDelete. A marked database
will be permanently deleted from the server.


 


Traditional
Domino database access privileges apply when using this function.  In order to
use NFSDbMarkForDelete on a database within a cluster, the remote Notes user
must have at least manager access privileges for the specified database;
otherwise, a database access error is returned.  Additionally, when called from
a remote session, the dbPathPtr argument must specify a qualified database
network pathname that can be constructed using the DNCanonicalize and
OSPathNetConstruct C API functions.


 


Only
use the NFSDbMarkForDelete function against databases that reside on a Lotus
Domino Server configured for a cluster.  If the server is not a member of a
cluster, the "pending deletion" option will be set, but the database
will not be deleted.  It is the Cluster Manager's responsibility to delete the
database after it is marked, and the Cluster Manager is only installed on
clustered Lotus Domino Servers.


 


For
more information, see the *Domino 5 Administration Help* database.


 


**Parameters :**



Input :  

dbPathPtr  -  Address of string containing the fully qualified database
pathname.   

  




Output :  

(routine)  -  If successful,  returns NOERROR; otherwise, returns database
access errors.  

  

  




 **Sample Usage :**



    ...


 


   
#include <nsfdb.h>


   
#include <dname.h>


   
#include <osfile.h>


    


    ...


 


     /\*
Canonicalize the Servername \*/  

    nError = DNCanonicalize( 0L, NULL, szServerName,   

                                szCanonServerName, MAXUSERNAME, NULL);  

               

    /\* Construct NetPath \*/  

    nError = OSPathNetConstruct (NULL, (char FAR \*)szServerName,   

                                (char FAR \*)szDBName, (char FAR
\*)szNetPathName);  

      

    /\* Warn the user, and mark for delete \*/  

    strcpy (szErrorString,  

           "Marking a database for deletion can not be undone.\nDo you
wish to continue?");  

       

    if ( MessageBox (GetFocus(), szErrorString, "Warning!", MB\_YESNO)
== IDYES)  

            nError = NSFDbMarkForDelete ( (char FAR \*)szNetPathName );


 


    ...


 


 **See Also :**


**[DBOPTION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0EE5CF1B5F5804FF852562900050AADD)**


**[DNCanonicalize](DNCanonicalize.md)**


**[NSFDbMarkInService](NSFDbMarkInService.md)**


**[NSFDbMarkOutOfService](NSFDbMarkOutOfService.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





