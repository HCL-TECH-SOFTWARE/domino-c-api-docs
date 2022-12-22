




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



**NSFDbMarkOutOfService** **- Marks a
database out of service.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbMarkOutOfService(**  

      const char far \*dbPathPtr**);**



**Description :**



The
NFSDbMarkOutOfService function marks a cluster database out of service for
remote user sessions by modifying the database option flags to include
DBOPTION\_OUT\_OF\_SERVICE.   When a call to NFSDbMarkOutOfService is successful, 
the Cluster Manager denies any new user sessions for this database.  This
restriction is in addition to any restrictions set forth in the database access
control list (ACL).  The purpose of this function is allow the system
administrator to perform maintenance on a database without requiring a server
shutdown or having to use the database ACL to restrict access.


 


In order to
use NFSDbMarkOutOfService with a database on a clustered server, the remote
Notes user must have at least designer access privileges.  If a user's
privilege level is insufficient, a database access error is returned.  


 


Additionally,
when called from a remote session, the dbPathPtr argument must specify a
qualified database network pathname that can be constructed using the
DNCanonicalize and OSPathNetConstruct C API functions.


 


The
NFSDbMarkOutOfService function affects only databases that reside on Domino
clusters.  You can mark a database back in service by calling the
NFSDbMarkInService function.


 


For more
information, see the *Domino Administration Help* database.


 


**Parameters :**



Input :  

dbPathPtr  -  Address of string containing fully qualified database pathname.  

  




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

      

    /\* Mark in service \*/  

    nError = NSFDbMarkOutOfService ( (char FAR \*)szNetPathName );


 


    ...


 


 **See Also :**


**[DBOPTION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0EE5CF1B5F5804FF852562900050AADD)**


**[DNCanonicalize](DNCanonicalize.md)**


**[NSFDbMarkForDelete](NSFDbMarkForDelete.md)**


**[NSFDbMarkInService](NSFDbMarkInService.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





