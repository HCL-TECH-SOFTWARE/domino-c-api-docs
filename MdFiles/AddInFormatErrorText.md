




<!--
 /\* Font Definitions \*/
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



**AddInFormatErrorText** **- Format an
error string.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNVARARGS **AddInFormatErrorText(**  

      char far \*retString,  

      char far \*String,  

      <Any 'C' type>  optional\_var1, ...**);**



**Description :**



AddInFormatErrorText
is used to generate a formatted error message.  The message can then be used by
the program for purposes other than standard AddIn logging, for example,
updating the status display (see AddInSetStatusText).    

  

It can also be used to format an error message that requires more than one
argument for its format string.  In this case, the formatted error string can
then be passed to AddInLogErrorText as the Arg parameter with a text string
containing a "%s" format specifier passed in as the String
parameter.  However, the function, AddInLogMessageText, provides an easier way
to accomplish this.  

  

The second parameter to AddInFormatErrorText is a string that may contain up to
four printf-type format specifiers.  If it does contain printf-type format
specifiers, the remaining parameters must be printf-type arguments that resolve
each of the format specifiers.  Up to 16 bytes of additional parameters may be
specified.  The print format specifiers supported by Domino are described in
the Tech Note "<notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9868F4BF0474BE9B85255F1A0072B0AB>[Domino Print Format Specifiers](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8D9526BA49EF953985255F1D0064F069)".  Tech
Notes are listed in the view, Reference Tools/Tech Notes.  

  

This function performs a function similiar to "sprintf".


 


**Parameters :**



Input :  

  

String  -  The error text string.  This string may contain up to four
printf-type (%) format specifiers. For each format specifier provided, there
should be an additional argument provided for formatting into the message
string.  

  

optional\_var1, ...  -  From 0 to 16 bytes of arguments of any type, each
corresponding to one of the format specifiers embedded in the string loaded by
the first argument. All pointer values must be "far".  Leave off this
parameter entirely (use only the first two arguments) if there are no format
specifiers in the format string.  

  




Output :  

(routine)  -  None  

  

  

retString  -  The formatted message string is placed in the specified character
buffer.  It is the caller's responsibility to allocate this buffer (MAXSPRINTF
bytes) prior to making the call.  

  




 **See Also :**


**[AddInLogErrorText](AddInLogErrorText.md)**


**[AddInSetStatusText](AddInSetStatusText.md)**


**[AddInLogMessageText](AddInLogMessageText.md)**


**[AddInFormatError](AddInFormatError.md)**



----------------------------------------------------------------------------------------------------------


 





