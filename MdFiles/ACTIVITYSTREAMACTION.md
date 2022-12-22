




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



**Data Type : Log**



**ACTIVITYSTREAMACTION** **-** Callback
function for activity logging


**----------------------------------------------------------------------------------------------------------**



**#include
<log.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR ACTIVITYSTREAMACTION)(


    const char
\*DescName, 


    DWORD DescIdx,


    DWORD Flags,


    WORD  PrimaryKey,


   const TIMEDATE\*
TimeStamp,


    void
\*pActivityRecord,


    void \*pUserData);


 


**Description :**



This is the
datatype of the action routine passed to LogEnumActivityStream.


 


 


DescName -     The
name of the activity type.


 


DescIdx -         The
index associated with an activity type. Although there is no permanent
association between the value of this field and DescName, it does remain
consistent during the lifetime of an activity stream. i.e between calls to
LogOpenActivityStream and LogCloseActivityStream 


 


Flags -                         Flags
associated with the record description. See ACTFLAGS\_


 


PrimaryKey -     If
the ACTFLAGS\_CHECKPOINTED\_RECORD flag is set, this param indicates the 0 based
index of the field that is the primary key of the record.


 


TimeStamp -     The
time that the record was created.


 


pActivityRecord 
-         Pointer to a buffer containing the record.  This buffer is in the
format of an ITEM\_TABLE.


 


pUserData -      User
context information


 


 **See Also :**


**[LogEnumActivityStream](LogEnumActivityStream.md)**



----------------------------------------------------------------------------------------------------------


 





