




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




 


**Symbolic Value : Statistics
Reporting**



**STATPKG\_xxx** **-** Facility
names for statistics reporting routines.


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**


 **Symbolic Values :**      STATPKG\_OS          -  Operating system facility.  

  

      STATPKG\_STATS   -  Statistics facility (eg: current time, start time).  

  

      STATPKG\_OSMEM   -  Memory facility (eg: memory allocated, memory free).  

  

      STATPKG\_OSSEM   -  Semaphore facility.  

  

      STATPKG\_OSSPIN   -  Spin facility  

  

      STATPKG\_OSFILE   -  Disk facility (eg: size of disk in bytes).  

  

      STATPKG\_SERVER             -  Server facility (eg: server name).  

  

      STATPKG\_REPLICA            -  Replica facility.  

  

      STATPKG\_MAIL       -  Mail facility.  

  

      STATPKG\_MAILBYDEST     -  Mail by destination facility.  

  

      STATPKG\_COMM    -  Communication facility.  

  

      STATPKG\_NSF        -  Database facility.  

  

      STATPKG\_NIF         -  Database index facility.  

  

      STATPKG\_TESTNSF           -  Test facility.  

  

      STATPKG\_OSIO      -  IO facility.  

  

      STATPKG\_NET        -  Network facility.  

  

      STATPKG\_OBJSTORE        -  Object store facility.  

  

      STATPKG\_AGENT   -  Agent manager facility.  

  

      STATPKG\_WEB       -  Web retriever facility.  

  

      STATPKG\_CAL        -  Schedule manager facility.  

  

      STATPKG\_SMTP     -  SMTP/MIME MTA facility.  

  

      STATPKG\_LDAP      -  LDAP facility.  

  

      STATPKG\_NNTP     -  Used by the NNTP Server.  

  

      STATPKG\_ICM        -  Used by the ICM Server.  

  

      STATPKG\_ADMINP             -  Used by Administration Process.  

  

      STATPKG\_IMAP      -  Used by IMAP Server.  

  

      STATPKG\_MONITOR          -  Monitor facility.  

  

      STATPKG\_POP3      -  Used by the POP3 Server.  

  

      STATPKG\_FT          -  Full text search facility  

  

      STATPKG\_DECS     -  Used by the DECS Server  

  

      STATPKG\_EVENT   -  Event facility.  

  

      STATPKG\_DB2NSF             -  Used by DB2NSF.  

  

      STATPKG\_FA          -  Fault analyzer.  

  




**Description :**



These values
specify facility names for the statistics reporting routines.


 **See Also :**


**[StatUpdate](StatUpdate.md)**


**[StatDelete](StatDelete.md)**


**[StatTraverse](StatTraverse.md)**


**[StatToText](StatToText.md)**



----------------------------------------------------------------------------------------------------------


 





