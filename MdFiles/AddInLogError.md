




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



**AddInLogError** **- Format
and write error message to the log file (uses string resources).**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNPUBLIC **AddInLogError(**  

      STATUS  StringID,  

      STATUS  AdditionalErrorCode,  

      char far \*Arg**);**



**Description :**



AddInLogError
formats an error message, displays it on the standard output, and appends the
message as new line to the "Events" field in a Miscellaneous Events
document in the Domino server or Notes client log.  The generated message has
the form:  

   

          <DATE>  <TIME>  <Primary status message>:
<Secondary status message>  

  

The first parameter, StringID, is a string resource ID that identifies a string
resource located in the calling program's resource module. The second
parameter, AdditionalErrorCode, may be another string resource ID, or it may be
the STATUS returned from a C API function.  

  

The string specified by StringID may contain a printf-type format specifier. If
it does, the last parameter, Arg, must point to a printf-type argument that
resolves the format specifier.  Only one format specifier argument is supported
in this function.  Use AddInLogMessage if more than one format specifier
argument is needed.  The print format specifiers supported by Domino are
described in the Tech Note "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B3E004F65FF)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  

  

AddInLogError formats the Primary status message using StringID and, optionally,
Arg.  It formats the Secondary status message using the error message
associated with the second parameter, AdditionalErrorCode.  

  

AddInLogError may be called from a NotesMain, main, or AddInMain API program.  

  

AddInLogError only supports errors that are stored as string resources and
therefore is not portable across all types of platforms.  Use the function,
AddInLogErrorText for platforms that do not support string resources.


 


When using
this function, you should call either AddInIdle or AddInIdleDelay on a regular
basis to flush the log entries from memory to disk and free up the memory.


 


**Parameters :**



Input :  

StringID  -  Primary status message string resource ID.  Corresponding message
string may contain up to one printf-type (%) format specifier which will get
formatted using the 3rd argument.  

  

AdditionalErrorCode  -  Secondary status code or message string resource ID. 
If not used, specify NOERROR.  

  

Arg  -  Pointer to an argument to be formatted into the  printf-type (%) format
specifier in the string specified by StringID. Specify NULL if primary message
string contains no format specifier.  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**


path\_name = argv[1];  

  

if (error = NSFDbOpen (path\_name, &db\_handle))  

{  

    AddInLogError(  

      ERR\_ADDIN\_CANTOPENDB,   /\* Error: unable to open database '%s' \*/  

      ERR(error),  

      path\_name);  

}


 **See Also :**


**[AddInFormatError](AddInFormatError.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[AddInLogMessage](AddInLogMessage.md)**


**[AddInLogMsg](AddInLogMsg.md)**


**[LogEvent](LogEvent.md)**


**[AddInLogErrorText](AddInLogErrorText.md)**



----------------------------------------------------------------------------------------------------------


 





