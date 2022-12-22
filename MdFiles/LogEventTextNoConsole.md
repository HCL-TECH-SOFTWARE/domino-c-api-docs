




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



**Function : Log**



**LogEventTextNoConsole** **- Same as
LogEventText, with no output to console**


**----------------------------------------------------------------------------------------------------------**



**#include <log.h>**



STATUS
LNVARARGS **LogEventTextNoConsole(**  

      char far \*String,  

      HANDLE  hModule,  

      STATUS  AdditionalErrorCode,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



This
function is similar to LogEventText and LogEvent, but does not display the
message to the standard output.


  

This function formats an error message, and enters it in the Domino Server or
Notes client log database, but does not display the message to the standard
output.  The generated message has the form:  

   

          <DATE>  <TIME>  <Primary status message>: <Secondary
status message>  

  

LogEventTextNoConsole is similar to AddInLogErrorText but more flexible. 
LogEventText uses the second argument, "hModule", to resolve the
third argument, "AdditionalErrorCode".  If
"AdditionalErrorCode" is a non-zero STATUS code returned from a C API
function, then you may be able to use AddInLogErrorText.  If
"AdditionalErrorCode" is a string in the calling program's resource
module, or some other resource module, then "hModule" must specify
the module containing that resource.  

  

The first parameter, "String", is the primary status message string. 
This string may contain printf-type (%) format specifiers.  For each format
specifier provided, there should be an additional argument provided for output,
starting with the fourth argument.  The print format specifiers supported by
Domino are described in the Tech Note "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/05621CA718E5605485255F1A006843EF)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  The third parameter,
"AdditionalErrorCode", may be another string resource ID, or it may
be the STATUS returned from a C API function.  The second parameter,
"hModule", specifies where "AdditionalErrorCode" is
resolved.  You may specify NULLHANDLE for the second parameter if
"AdditionalErrorCode" is resolved by Domino or by the calling
program.


 


When using
this function, you should call either AddInIdle or AddInIdleDelay on a regular
basis to flush the log entries from memory to disk and free up the memory.


 


**Parameters :**



Input :  

String  -  Primary status message string.  

  

hModule  -  A module handle of the module containing the string resource
identified by error\_status. If error\_status is a Domino error code,
module\_handle may be NULLHANDLE.  

  

AdditionalErrorCode  -  A STATUS code returned by an API function or the string
ID of a secondary error message.  NOERROR is an acceptable value.  

  

optional\_var1, ...  -  From 0 to 24 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the string loaded by
the first argument.  All pointer values must be "far".  Leave off
this parameter entirely (use only the above 3 arguments) if there are no format
specifiers in the Primary status message string.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully logged the event.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
obtain the error message.  

  

  




 **Sample Usage :**


if (error =
LogEventTextNoConsole("Unable to open input file %s.",  

        NULLHANDLE, NOERROR, (char far \*) szFileName))  

   goto Exit;


 **See Also :**


**[AddInFormatErrorText](AddInFormatErrorText.md)**


**[AddInLogErrorText](AddInLogErrorText.md)**


**[LogCloseEntry](LogCloseEntry.md)**


**[LogCompleteEntry](LogCompleteEntry.md)**


**[LogCreateEntry](LogCreateEntry.md)**


**[LogEvent](LogEvent.md)**


**[LogEventText](LogEventText.md)**



----------------------------------------------------------------------------------------------------------


 





