




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




**Initial Release 5.0.7**



**Function : Mail Gateway**



**MailAddMessageBodyTextExt** **- Converts
a text file and adds it as body item(s) to a message, allowing use of NLS\_INFO
structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailAddMessageBodyTextExt(**  

      DHANDLE  hMessage,  

      char far \*ItemName,  

      char far \*InputFileName,  

      DWORD  FontID,  

      char far \*LineDelim,  

      WORD  ParaDelim,  

      NLS\_PINFO  pInfo**);**



**Description :**



This
function converts a text file to composite text and adds it as body item(s) to
a message, allowing the use of the NLS\_INFO structure.  This function creates
multiple items of the same name and therefore is not limited to 64KB of input.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemName  -  Text item name (null-terminated).  Optional - NULL is
"Body".  

  

InputFileName  -  Input file name string (null-terminated).  

  

FontID  -  Font ID to be used.  Optional - 0 is 10pt Helv.  

  

LineDelim  -  Line delimiter characters (e.g. "\r\n").  Optional -
NULL is "" or null-terminated.  If the line delimiter character is
not NULL, and if a line contains one or more null characters, this line will be
ignored.  

  

ParaDelim  -  Paragraph delimiter flags (PARADELIM\_xxx).  Optional - 0 is
PARADELIM\_ANYBLANKLINE.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  (NULL if body text already
in the Lotus Multibyte Character Set (LMBCS)).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

  




 **See Also :**


**[MailCreateBodyItem](MailCreateBodyItem.md)**


**[MailAppendBodyItemLine](MailAppendBodyItemLine.md)**



----------------------------------------------------------------------------------------------------------


 





