




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



**NSFDbMarkInService** **- Marks a
database in service for remote user sessions.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbMarkInService(**  

      const char far \*dbPathPtr**);**



**Description :**



The
NFSDbMarkInService function marks a cluster database in service by clearing the
database option flag  DBOPTION\_OUT\_OF\_SERVICE, if set.   When a call to
NFSDbMarkInService is successful, the Cluster Manager enables users to access
the database again by removing the "out of service" access restriction. 



 


Traditional
Domino database access control list (ACL) privileges apply under all
circumstances. In order to use NFSDbMarkInService on a database in a cluster,
the remote Notes user must have at least designer access privileges for the
specified database. If a user does not have the proper privileges, a database
access error is returned.  


 


Additionally,
when called from a remote session, the dbPathPtr argument must specify a
qualified database network pathname that can be constructed using the
DNCanonicalize and OSPathNetConstruct C API functions.


 


The
NFSDbMarkInService function only affects databases within a Lotus Domino Server
cluster.


 


For
more information, see the *Domino  Administration Help* database.


 


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

    nError = NSFDbMarkInService ( (char FAR \*)szNetPathName );


 


    ...


 


 **See Also :**


**[DBOPTION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0EE5CF1B5F5804FF852562900050AADD)**


**[DNCanonicalize](DNCanonicalize.md)**


**[NSFDbMarkForDelete](NSFDbMarkForDelete.md)**


**[NSFDbMarkOutOfService](NSFDbMarkOutOfService.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





