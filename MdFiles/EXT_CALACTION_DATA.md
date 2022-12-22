




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




**Initial Release 9.0**



**Data Type : iCalendar**



**EXT\_CALACTION\_DATA** **-** Additional
data required to perform some actions


**----------------------------------------------------------------------------------------------------------**



**#include
<calapi.h>**



**Definition :**



**|** typedef struct
EXT\_CALACTION\_DATA


{


        WORD
wLen;                                           // MUST be
sizeof(EXT\_CALACTION\_DATA) - allows for safe expansion of struct in the future


        char\*
pszDelegateTo;                  // Required for dwAction: CAL\_PROCESS\_DELEGATE
- disregarded otherwise


        TIMEDATE\*
ptdChangeToStart;           // Desired new start date/time.  Required for
dwAction: CAL\_PROCESS\_COUNTER - disregarded otherwise


        TIMEDATE\*
ptdChangeToEnd;             // Desired new end date/time.  Required for
dwAction: CAL\_PROCESS\_COUNTER - disregarded otherwise


        BOOL\*
pfKeepInformed;                 // If populated for CAL\_PROCESS\_DELEGATE or
CAL\_PROCESS\_DECLINE, used to inform the Chair if 


                                                                    //
you want to keep informed.  


                                                                    //
If populated for CAL\_PROCESS\_COUNTER, used to keep a placeholder entry on the
Calendar.


                                                                    //
Disregarded otherwise.  


                                                                    //
NULL pointer means use default from user preferences.


        void\*
pReserved;                             // RESERVED - MUST be NULL


        LIST\*
pAddNamesReq;                          //new in 9.0.1. List of users to add to
the specified entry (or entries) as a Required attendee.  


                                                                    //
MUST be NULL if not adding anyone as required.  Only used by
CAL\_PROCESS\_UPDATEINVITEES.


        LIST\*
pAddNamesOpt;                          //new in 9.0.1.  List of users to add to
the specified entry (or entries) as an Optional attendee.  


                                                                    //
MUST be NULL if not adding anyone as optional.  Only used by
CAL\_PROCESS\_UPDATEINVITEES.


        LIST\*
pAddNamesFYI;                          //new in 9.0.1.  List of users to add to
the specified entry (or entries) as an FYI attendee.  


                                                                    //
MUST be NULL if not adding anyone as FYI.  Only used by CAL\_PROCESS\_UPDATEINVITEES.


        LIST\*
pRemoveNames;                          //new in 9.0.1.  List of users to remove
from the specified entry (or entries).  


                                                                    //
MUST be NULL if not removing anyone.  Only used by CAL\_PROCESS\_UPDATEINVITEES.


}
\*PEXT\_CALACTION\_DATA;


 


 




----------------------------------------------------------------------------------------------------------


 





