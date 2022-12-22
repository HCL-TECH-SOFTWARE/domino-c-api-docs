




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



**AddInLogMessage** **- Format
and write a message to the log file (uses string resources).**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNVARARGS **AddInLogMessage(**  

      STATUS  StringID,  

      STATUS  AdditionalErrorCode,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



This
function formats a message, displays it on the standard output, and appends the
message as new line to the "Events" field in a Miscellaneous Events
document in the Domino server or Notes client log.  The generated message has
the form:  

   

          <DATE>  <TIME> <Primary status message>:
<Secondary status message>  

  

The first parameter, StringID, is a resource ID that identifies a string
resource located in the calling program's resource module.   The second
parameter, AdditionalErrorCode, may be another string resource ID, or it may be
the STATUS returned from a C API function.  

  

The string specified by StringID may contain up to six printf-type format
specifiers. If it does contain printf-type format specifiers, the last
remaining parameters must be printf-type arguments that resolve each of the
format specifiers.  Up to 24 bytes of additional parameters may be specified. 
Pointer arguments, such as the addresses of strings, must be "far"
pointers.  The print format specifiers supported by Domino are described in the
Tech Note "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B3D007AC76B)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  

  

AddInLogMessage formats the Primary status message using StringID and the last
remaining parameters as described above.  It formats the Secondary status
message using the error message associated with the second parameter,
AdditionalErrorCode.    

  

This routine only supports errors that are stored as string resources and
therefore is not portable across all types of platforms.  Use the function,
AddInLogMessageText for platforms that do not support string resources.


 


When using
this function, you should call either AddInIdle or AddInIdleDelay on a regular
basis to flush the log entries from memory to disk and free up the memory.


 


**Parameters :**



Input :  

StringID  -  Primary status message string resource ID. The string may contain
up to six printf-type (%) format specifiers. For each format specifier, a
corresponding argument must be specified after the AdditionalErrorCode argument
to resolve the format specifier.  

  

AdditionalErrorCode  -  Secondary status code or message string resource ID. 
If not used, specify NOERROR.  

  

optional\_var1, ...  -  From 0 to 24 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the format string
associated with the StringID argument.  All pointer values must be
"far".  Leave off this parameter entirely (use only the above 2
arguments) if there are no format specifiers in the format string.  

  




Output :  

(routine)  -  None  

  

  




 **Sample Usage :**


[from .RC file]  

#define MSG\_INDEX\_DONE    PKG\_ADDIN+126  

  

[from .RC file, string table]  

  

MSG\_INDEX\_DONE, "Indexed %lu documents (%lu bytes) in %s"  

  

  

[from .C file]  

if (!error)  

{  

  

     

AddInLogMessage(MSG\_INDEX\_DONE, NOERROR,  

      Stats.DocsAdded + Stats.DocsUpdated + Stats.DocsDeleted,  

      Stats.BytesIndexed,  

      CTX->FileName);  

}


 **See Also :**


**[AddInLogError](AddInLogError.md)**


**[AddInLogMessageText](AddInLogMessageText.md)**


**[AddInLogMsg](AddInLogMsg.md)**


**[AddInSetStatus](AddInSetStatus.md)**



----------------------------------------------------------------------------------------------------------


 





