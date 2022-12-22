




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




 


**Function : OS Strings**



**OSTranslate** **-
Translates a string to/from the native character set and LMBCS.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**



WORD
LNPUBLIC **OSTranslate(**  

      WORD  TranslateMode,  

      const char far \*In,  

      WORD  InLength,  

      char far \*Out,  

      WORD  OutLength**);**



**Description :**



OSTranslate
translates a string between the specified character set and Lotus Multi-Byte
Character Set (LMBCS) optimized for Group 1.  The character set is specified in
the TranslateMode parameter.  

  

LMBCS optimized for Group 1 is the format used for all input and output to the
API. (And is also the format in which all Domino and Notes strings are stored
internally.)   

  

LMBCS is composed of a set of character "groups", with the leading
byte of each character indicating the group that the character is in. A string
may be optimized for a particular group, in which case characters in that group
are stripped of their initial byte.   

  

Since Domino and Notes use LMBCS optimized for Group 1, every character in
Domino and Notes is assumed to be in Group 1 unless it begins with a byte
indicating otherwise. Japanese characters, for instance, are not in Group 1 so
within Domino and Notes they begin with a byte indicating their group.


 


For UNICODE,
only the UTF-8 and UTF-16 encodings are supported.  Any UNICODE character
string supplied to OSTranslate will need to be in UTF-16 format:  16-bit
characters packed together on 16-bit boundaries. 


 


**Parameters :**



Input :  

TranslateMode  -  A flag to control which direction the input string is
translated, either LMBCS to the specified character set or the specified
character set to LMBCS. The flags are described in the symbol set
OS\_TRANSLATE\_xxx.  

  

In  -  The string to be translated.  

  

InLength  -  The size of the input string in bytes, or MAXWORD.  

  

OutLength  -  The size of the output buffer in bytes, or MAXPATH.  

  




Output :  

(routine)  -  The number of bytes used to store the return data in the output
buffer.  

  

  

Out  -  Buffer to receive output.  

  




 **See Also :**


**[OSLoadString](OSLoadString.md)**


**[OS\_TRANSLATE\_xxx](OS_TRANSLATE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





