




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



**Symbolic Value : Log**



**ACTFLAGS\_xxx** **-** Public
activity logging API flags.


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**


 **Symbolic Values :**      ACTFLAGS\_CHECKPOINTED\_RECORD      -  Used with the
ACTIVITYSTREAMACTION callback routine. Indicates that a record is a
checkpointed record. Passed via the ActionRoutine  

  

      ACTFLAGS\_CHECKPOINT\_FINAL   -  Used with the ACTIVITYSTREAMACTION
callback routine. Indicates that a record is the final record in a series of
checkpointed records.  

  

      ACTFLAGS\_COLLAPSE\_CHECKPOINTS    -  Used with LogOpenActivityStream.
Causes the LogEnumActivityStream function to pass only the last known instance
of a checkpointed record to the ActionRoutine. Note that this does not imply
that all checkpoint records passed will be the final record in the series.  

  

      ACTFLAGS\_RECORD\_TRUNCATED            -  Passed via the stream callback
function flags argument. Indicates that the record was truncated. Current
record size limit is 20K.  

  




 **See Also :**


**[ACTIVITYSTREAMACTION](ACTIVITYSTREAMACTION.md)**


**[LogEnumActivityStream](LogEnumActivityStream.md)**


**[LogOpenActivityStream](LogOpenActivityStream.md)**



----------------------------------------------------------------------------------------------------------


 





