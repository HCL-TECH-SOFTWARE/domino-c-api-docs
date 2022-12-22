




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




**Initial Release 6**



**Function : Log**



**LogEnumActivityStream** **-
Enumerates the set of server activity records in an activity logging stream**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNPUBLIC **LogEnumActivityStream(**  

      void \*pStreamCtx,  

      ACTIVITYSTREAMACTION  ActionRoutine,  

      void \*pUserData,  

      ACTIVITYSTREAMPOSITION \*Position,  

      DWORD  PositionSize**);**



**Description :**



This
function enumerates the set of server activity records that are referenced in
an activity logging stream.  For every record that is processed in the stream,
a caller-supplied callback function is called.


 


**Parameters :**



Input :  

pStreamCtx  -  A pointer to the stream context of the open activity logging
stream, as returned by LogOpenActivityStream()  

  

ActionRoutine  -  A caller provided function that is called to for every record
in the stream  

  

pUserData  -  User provided context information  

  

PositionSize  -  If a position parameter is passed, then this field is
required. It should be sizeof(ACTIVITYSTREAMPOSITION). If no position is
passed, the value should be set to zero (0).  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully enumerated activity stream.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

Position  -  If desired, a caller provided ACTIVITYSTREAMPOSITION structure
will be updated with the position where processing stopped. This structure can
be used by LogSetActivityStreamPosition to resume processing at the record
indicated by this structure.  Set to NULL if you don't need to save the stream
position  

  




 **See Also :**


**[ACTIVITYSTREAMACTION](ACTIVITYSTREAMACTION.md)**


**[ACTIVITYSTREAMPOSITION](ACTIVITYSTREAMPOSITION.md)**


**[LogOpenActivityStream](LogOpenActivityStream.md)**



----------------------------------------------------------------------------------------------------------


 





