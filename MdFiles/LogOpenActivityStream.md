




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



**LogOpenActivityStream** **- Open a
stream for activity logging**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNPUBLIC **LogOpenActivityStream(**  

      void \*\*pStreamCtx,  

      const char \*ServerName,  

      const char \*LogPath,  

      const char \*ActivityName,  

      DWORD  Flags,  

      const TIMEDATE\_PAIR \*DateRange**);**



**Description :**



This
function opens a stream which is used to read activity logging data


 


**Parameters :**



Input :  

  

ServerName  -  A pointer to the null-terminated name of the Lotus Domino Server
you want to access.  Information on servers is available from the Domino
Directory (Server's Address book) using standard NIF and NSF APIs.  The string
should be no longer than MAXUSERNAME. If you want to specify "no
server" (the local machine), pass NULL or a pointer to "" (the
null string).  

  

LogPath  -  A pointer to the null-terminated log path.  

  

ActivityName  -  A pointer to the null-terminated names of the activity types
you wish to extract. Multiple activity names can be concatenated with the
"|" character. The "\*" character works as a wildcard.  You
may also extract all activity types by passing NULL  

  

Flags  -  ACTFLAGS\_COLLAPSE\_CHECKPOINTS causes only the latest instance of a
checkpointed record to be output. Note that this means that records may not be
output in sequential order.  

  

DateRange  -  The lower and upper time bounds of the activity you which to
process. To process all available records set Lower to TIMEDATE\_MINIMUM and
Upper to TIMEDATE\_MAXIMUM or pass NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully opened activity stream.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

pStreamCtx  -  A pointer to the stream context needed by the other API
functions.  

  




 **See Also :**


**[ACTFLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FB388D6D3538978F85256A2B004EC4D9)**


**[ACTIVITYSTREAMACTION](ACTIVITYSTREAMACTION.md)**


**[ACTIVITYSTREAMPOSITION](ACTIVITYSTREAMPOSITION.md)**


**[LogCloseActivityStream](LogCloseActivityStream.md)**


**[LogEnumActivityStream](LogEnumActivityStream.md)**


**[LogSetActivityStreamPosition](LogSetActivityStreamPosition.md)**



----------------------------------------------------------------------------------------------------------


 





