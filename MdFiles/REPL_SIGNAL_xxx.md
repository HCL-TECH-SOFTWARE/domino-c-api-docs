




<!--
 /\* Font Definitions \*/
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




**Initial Release 5.0.2**



**Symbolic Value : Replication**



**REPL\_SIGNAL\_xxx** **-** Definitions
for replication state signal handler


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**


 **Symbolic Values :**      REPL\_SIGNAL\_IDLE            -  indicating the connection is
done.  

  

      REPL\_SIGNAL\_PICKSERVER          -  Display that it is trying to select a
server.  

  

      REPL\_SIGNAL\_CONNECTING         -  Starting the connection.  

  

      REPL\_SIGNAL\_SEARCHING            -  Searching for matching replica on the
server.  

  

      REPL\_SIGNAL\_SENDING    -  A "push" replication.  

  

      REPL\_SIGNAL\_RECEIVING             -  A "pull" replication.  

  

      REPL\_SIGNAL\_SEARCHINGDOCS              -  Replicator is in the searching
phase.  

  

      REPL\_SIGNAL\_DONEFILE   -  Signal the file is done.  

  

      REPL\_SIGNAL\_REDIRECT   -  Signal found a redirect.  

  

      REPL\_SIGNAL\_BUILDVIEW             -  Signal view is building.  

  




 **See Also :**


**[OSSIGREPLPROC](OSSIGREPLPROC.md)**



----------------------------------------------------------------------------------------------------------


 





