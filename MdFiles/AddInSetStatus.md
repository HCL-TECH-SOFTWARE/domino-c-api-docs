




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
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
a:link, span.MsoHyperlink
 {color:#0563C1;
 text-decoration:underline;}
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



**AddInSetStatus** **- Set the
status string of a Server Add-in task's default status line. Uses string
resources.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNVARARGS **AddInSetStatus(**  

      STATUS  StringID,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



This
function formats a string and sets the status string of the current add-in
task's default status line to the formatted string.  

  

A status line is one line of text displayed by the Lotus Domino Server console
in response to the "show tasks" command.  Each status line consists
of a task name (in the left column) and a status string (in the right column).  

  

Domino creates a default status line for add-in tasks that use AddInMain() as
the entry point.  AddInSetStatus() sets the status string of the current add-in
task's default status line.  

  

AddInSetStatus() formats a status string based on the parameters. The StringID
parameter is a string resource ID that identifies a string in the string table
attached to the calling program's executable file.  The string may contain up
to four printf-type format specifiers.  If it does contain printf-type format
specifiers, the remaining parameters must be printf-type arguments that resolve
each of the format specifiers.  Up to 12 bytes of additional parameters may be
specified.  This function performs a function similar to "printf",
except that it works with Domino string resources.  Pointer arguments, such as
pointers to "C" strings, must be "far" pointers.  The print
format specifiers supported by Domino are described in the Tech Note "<notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4F6BE4BFB5BFBB6285255F1D0069AC5D>[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B3E004F65FF)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  

  

This function has no effect unless called from a Lotus Domino Server add-in
task.   

  

This function only supports message strings that are stored as string resources
and therefore is not portable across all types of platforms.  Use the function,
AddInSetStatusText() for platforms that do not support string resources.


 


**Parameters :**



Input :  

StringID  -  Resource ID of string describing Addin's current
"state".  The string may contain up to four printf-type (%) format
specifiers.  For each format specifier, a corresponding argument must be
specified to resolve the format specifier.  

  

optional\_var1, ...  -  From 0 to 12 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the format string
associated with the StringID argument.  All pointer values must be
"far".  Leave off this parameter entirely (use only the above
argument) if there are no format specifiers in the format string.  

  




Output :  

(routine)  -  None  

  

  




 **Sample Usage :**


  

/\* Constants & corresponding Strings built into AddIn's string table.\*/  

/\* #define MSG\_SMKADDN\_RUNNING                    (PKG\_ADDIN+9)      \*/  

/\*        msgtext(MSG\_SMKADDN\_RUNNING,           "Running")         
\*/  

  

   /\* Set task status to "Running" for server console \*/  

  

   AddInSetStatus(MSG\_SMKADDN\_RUNNING);  

  




 **See Also :**


**[AddInSetStatusText](AddInSetStatusText.md)**


**[AddInMain](AddInMain.md)**


**[AddInFormatError](AddInFormatError.md)**


**[AddInLogError](AddInLogError.md)**


**[AddInLogMsg](AddInLogMsg.md)**



----------------------------------------------------------------------------------------------------------


 





