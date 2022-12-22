




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




**Initial Release 6**



**Data Type : Backup**



**NOTERESTORECALLBACKFUNCTION** **-** Definition
of the note restore callback function that the backup/archive utility will have
to provide for monitoring notes during Media Recovery.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR NOTERESTORECALLBACKFUNCTION)(     


        DWORD
state\_flags, 


        void
far \* userParm, 


        NOTE\_RESTORE\_CALLBACK\_INFO
far \* info);


 


**Description :**



During media
recovery, this callback function is implemented with the following parameters: 



 


inputs:


state\_flags
- The state flag which describes the action taken on a particular note during
the media recovery process.  See MediaCallbackFlags.


 


userParm -
User information (e.g.  NoteID, UserName, etc.) supplied to
NSFRecoverDatabasesWIthCallback to be passed to NOTERESTORECALLBACKFUNCTION  to
narrow the scope of the callback routine.  Zero to return information for all
notes updated. 


 


info -
Pointer to the structure which contains information regarding each note updated
during the media recovery process.  See NOTE\_RESTORE\_CALLBACK\_INFO.


 


outputs: 


STATUS -
Status of the call: NOERROR. Any other status indicates an error condition.


 **See Also :**


**[MediaCallbackFlags](MediaCallbackFlags.md)**


**[NOTE\_RESTORE\_CALLBACK\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F74757EF9FF9B2CD85256AD100521EF5)**


**[NSFRecoverDatabasesWithCallback](NSFRecoverDatabasesWithCallback.md)**



----------------------------------------------------------------------------------------------------------


 





