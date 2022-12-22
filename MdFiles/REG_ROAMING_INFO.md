




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




**Initial Release 7.0**



**Data Type : User Registration**



**REG\_ROAMING\_INFO** **-** Structure
that defines roaming registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD   Size;                  /\*
size of this structure - must initialize with sizeof (REG\_ROAMING\_INFO) \*/


        char    \*ServerName;           /\*      server
destination for three roaming files \*/


        char    \*SubDirectory;         /\*      path
(relative) to data dir on which roaming files will be created \*/


        WORD    CleanupSetting;               /\*      REG\_ROAMING\_CLEANUP\_NEVER
is don't cleanup


                                                     REG\_ROAMING\_CLEANUP\_EVERY\_NDAYS
is cleanup every ndays


                                                     REG\_ROAMING\_CLEANUP\_AT\_SHUTDOWN
is cleanup at shutdown


                                                     REG\_ROAMING\_CLEANUP\_PROMPT
is prompt for cleanup\*/


        WORD    CleanupPeriod;         /\*      for
REG\_ROAMING\_CLEANUP\_EVERY\_NDAYS - days, values 1 through 365 allowed \*/


        DHANDLE hReplicaServers;       /\*
text list of replica servers \*/


       WORD    OnDuplicate;           /\*
one of REG\_FILE\_DUP\_XXX \*/


 


        DWORD   Reserved[4];


        void    \*pReserved[4];


        }
REG\_ROAMING\_INFO;


 


 


 


**Description :**




This
structure defines roaming registration information for the REGNewPerson
function.  The entire structure must be initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                        Size
of this structure - must be initialized with sizeof (REG\_ROAMING\_INFO).


ServerName           Destination
server name for the roaming files.


SubDirectory          Path
(relative) to data dir on which roaming files will be created.


CleanupSetting       The
cleanup setting used by the roaming client (see REG\_ROAMING\_CLEANUP\_XXX).


CleanupPeriod        Number
of days between cleanup (1 - 365) for REG\_ROAMING\_CLEANUP\_EVERY\_NDAYS.


hReplicaServers     (Optional.)
Handle to a text list of server names where replica stubs of the roaming files
should be created.  The list should be constructed with ListAllocate and
ListAddEntry.  


    OnDuplicate      one
of REG\_FILE\_DUP\_XXX.


   
Reserved                Reserved - must be 0.


pReserved              Reserved
- must be NULL.


 


 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAllocate](ListAllocate.md)**


**[REGNewPerson](REGNewPerson.md)**


**[REG\_FILE\_DUP\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/F5B76F9FC1F19DDE4825709C005227B9)**


**[REG\_ROAMING\_CLEANUP\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/A87BC2927E58A81285256EBD005236A8)**



----------------------------------------------------------------------------------------------------------


 





