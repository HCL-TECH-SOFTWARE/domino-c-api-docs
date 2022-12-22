




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : AddIn**



**AddInLogMsg** **- Format
and write a message to the log file (uses string resources).**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNPUBLIC **AddInLogMsg(**  

      STATUS  StringID,  

      char far \*Arg**);**



**Description :**



AddInLogMsg
formats an error message, displays it on the standard output, and appends the
message as new line to the "Events" field in a Miscellaneous Events
document in the  Domino server or Notes client log.  The generated message has
the form:  

   

          <DATE>  <TIME> <status message>  

  

The first parameter, StringID, is a resource ID. It must identify a string
resource located in the calling program's resource module. The string specified
by StringID may contain one printf-type format specifier. If it does, the
second parameter, Arg, must point to a printf-type argument that resolves the
format specifier.  Only one format specifier argument is supported in this
function.  Use AddInLogMessage if more than one format specifier argument is
needed.  The print format specifiers supported by Domino are described in the
TechNote "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B3D007AC76B)".  

  

Use AddInLogMsg to log events that are not associated with a STATUS code
returned from a C API function. AddInLogMsg is a macro that calls
AddInLogError:  

  

     #define AddInLogMsg(s, e) AddInLogError(s, NOERROR, e)  

  

 AddInLogMsg may be called from a NotesMain, main, or AddInMain API program. 


 


When using
this function, you should call either AddInIdle or AddInIdleDelay on a regular
basis to flush the log entries from memory to disk and free up the memory.


 


**Parameters :**



Input :  

StringID  -  Resource ID of string to be formatted.  The string may contain up
to one printf-type (%) format specifier.  If a format specifier is present, a
second argument must be provided for formatting into the message string.  

  

Arg  -  Pointer to an argument to be formatted into the  printf-type (%) format
specifier in the string specified by StringID.  Specify NULL if the string
contains no format specifier.  

  




Output :  

(routine)  -  None  

  

  




 **Sample Usage :**


/\* #define
MSG\_SMKADDN\_STARTED                     (PKG\_ADDIN+11)    \*/  

/\*    msgtext(MSG\_SMKADDN\_STARTED, "Smoke Addin Example Started up")
\*/  

     

/\* Log the task status: message appears on console display and  \*/  

/\* in Miscellaneous "Events" View in the server's LOG.NSF       \*/  

  

AddInLogMsg(MSG\_SMKADDN\_STARTED);


 **See Also :**


**[AddInLogError](AddInLogError.md)**


**[AddInLogMessage](AddInLogMessage.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[AddInFormatError](AddInFormatError.md)**


**[LogEvent](LogEvent.md)**



----------------------------------------------------------------------------------------------------------


 





