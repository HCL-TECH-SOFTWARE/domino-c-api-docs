




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




**Initial Release 4.0**



**Function : Mail Gateway**



**MailLogEventText** **- Add an
event to the mail logs using a character string.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNVARARGS **MailLogEventText(**  

      WORD  Flags,  

      char \*String,  

      HMODULE  hModule,  

      STATUS  AdditionalErrorCode,  

      <Any 'C' type>  [optional arguments]...**);**



**Description :**



Log a mail
gateway event.  This function is almost identical to MailLogEvent();  the
second parameter is a pointer to a character string instead of a string
resource ID.  Use MailLogEventText instead of MailLogEvent if your program
works in environments where Windows-style resources are not available (such as
Unix).


 


The
"Flags" parameter controls which logs will be used;  for details, see
the entry MAIL\_LOG\_xxx.  The String parameter contains the primary status
message;  this string may also contain printf-type (%) format specifiers.  For
each format specifier provided, there should be an additional argument provided
for output, starting with the fifth argument.  The print format specifiers
supported by Domino are described in the Tech Note "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4C2995E2A76B550A85255F6B00459570)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  The parameter
AdditionalErrorCode is used to select a secondary status message string which
is appended to the log message.


 


This
function formats an error message, displays it on the standard output, and
enters it in the selected logs.  The generated message has the form:  

   

          <DATE>  <TIME>  <Primary status message>:
<Secondary status message>


 


When using
this function, you should call either AddInIdle or AddInIdleDelay on a regular
basis to flush the log entries from memory to disk and free up the memory.


 


**Parameters :**



Input :  

Flags  -  Mail logging control flags.  See the entry MAIL\_LOG\_xxx for details.  

  

String  -  Pointer to a null-terminated primary status message string.  The
message string may contain printf-type (%) format specifiers.  For each format
specifier provided, there should be an additional argument provided for output,
starting with the fifth argument.  

  

hModule  -  A module handle of the module containing the string resources.  

  

AdditionalErrorCode  -  A STATUS code to return to the Server.  If there is no
additional status information, a value of NOERROR is an acceptable argument.  

  

[optional arguments]...  -  From 0 to 24 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the string loaded by
the second argument.  All pointer values must be "far".  Leave off
this parameter entirely (use only the above 4 arguments) if there are no format
specifiers in the format string.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Log message recorded.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  




 **See Also :**


**[LogEventText](LogEventText.md)**


**[MailLogEvent](MailLogEvent.md)**


**[MAIL\_LOG\_xxx](MAIL_LOG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





