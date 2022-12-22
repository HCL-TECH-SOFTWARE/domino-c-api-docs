




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



**AddInFormatError** **- Format an
error string (uses string resources).**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNVARARGS **AddInFormatError(**  

      char far \*retString,  

      STATUS  StringID,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



AddInFormatError
is used to generate a formatted error message.  The message can then be used by
the program for purposes other than standard AddIn logging, for example,
updating the status display (see AddInSetStatus).    

  

It can also be used to format error messages that require more than one
argument for its format string.  In this case, the formatted error string can
then be passed to AddInLogError as the Arg parameter, with a string resource id
that is associated with a text string containing a "%s" format
specifier passed in as the StringID parameter.  However, the function,
AddInLogMessage, provides an easier way to accomplish this.  

  

The second parameter, StringID,  is a resource ID that identifies a string
resource located in the calling program's resource module.  The string
specified by StringID may contain up to four printf-type format specifiers.  If
it does contain printf-type format specifiers, the remaining parameters must be
printf-type arguments that resolve each of the format specifiers.  Up to 16
bytes of additional parameters may be specified.  The print format specifiers
supported by Domino are described in the Tech Note. "[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B3D007AC76B)". Tech Notes
are listed in the view, Reference Tools/Tech Notes.  

    

This function performs a function similiar to "sprintf", except that
it works with Domino string resources.  

  

This routine only supports errors that are stored as string resources and
therefore is not portable across all types of platforms.  Use the function,
AddInFormatErrorText for platforms that do not support string resources.


 


**Parameters :**



Input :  

  

StringID  -  Resource ID of string to be formatted. The string may contain up
to four printf-type (%) format specifiers. For each format specifier provided,
there should be an additional argument provided for formatting into the message
string.  

  

optional\_var1, ...  -  From 0 to 16 bytes of arguments of any type, each corresponding
to one of the format specifiers embedded in the format string associated with
the StringID argument.  All pointer values must be "far". Leave off
this parameter entirely (use only the above 2 arguments) if there are no format
specifiers in the format string.  

  




Output :  

(routine)  -  None.  

  

  

retString  -  The formatted message string is placed in the specified character
buffer.  It is the caller's responsibility to allocate this buffer (MAXSPRINTF
bytes) prior to making the call.  

  




 **Sample Usage :**


  

            /\* Create a 3 string arg error\_msg from 3 numeric values\*/  

            sprintf(scratch\_str1, "%lf", day\_double);  

            sprintf(scratch\_str2, "%lf", min\_double);  

            sprintf(scratch\_str3, "%lf", sec\_double/20.0);  

            AddInFormatError(error\_msg, MSG\_SMKADDN\_STATS,  

                            scratch\_str1, scratch\_str2, scratch\_str3);  

            AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

  


 **See Also :**


**[AddInLogError](AddInLogError.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[AddInLogMsg](AddInLogMsg.md)**


**[AddInLogMessage](AddInLogMessage.md)**


**[AddInFormatErrorText](AddInFormatErrorText.md)**



----------------------------------------------------------------------------------------------------------


 





