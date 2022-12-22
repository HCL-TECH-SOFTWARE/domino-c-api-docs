




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




 


**Symbolic Value : Compound Text**



**COMP\_xxx** **-** CompoundTextXxx
() Control Flags


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**


 **Symbolic Values :**      COMP\_FROM\_FILE              -  CompoundText is derived from
a file.  

  

      COMP\_PRESERVE\_LINES   -  Insert a line break (0) for each line delimiter
found in the input text buffer. This preserves input line breaks.  

  

      COMP\_PARA\_LINE              -  Create a new paragraph for each line
delimiter found in the input text buffer.  

  

      COMP\_PARA\_BLANK\_LINE             -  Create a new paragraph for each blank
line found in the input text buffer. A blank line is defined as a line
containing just a line delimiter (specified by the pszLineDelim parameter to
CompoundTextAddTextExt).  

  

      COMP\_SERVER\_HINT\_FOLLOWS   -  A "hint" follows the comment for
a document link. If this flag is set, the pszComment argument points to the
comment string, the terminating NUL ('\0'), the hint string, and the
terminating NUL.  

  




**Description :**



The flags
COMP\_FROM\_FILE, COMP\_PRESERVE\_LINES, COMP\_PARA\_LINE, and COMP\_PARA\_BLANK\_LINE
control the way CompoundTextAddTextExt parses the input text buffer (or file)
to create a sequence of CD records. Combine these flags by bitwise OR-ing them
together.  

  

If the COMP\_FROM\_FILE flag is clear, CompoundTextAddTextExt adds the number of
text characters specifed by the dwTextLen parameter and starting at the address
specified by the pchText parameter to the compound text context.  If the
COMP\_FROM\_FILE flag is set, CompundTextAddTextExt treats the text specified by
pchText as the name of a file, and the dwTextLen parameter is ignored. 
CompundTextAddTextExt opens and reads the specified file, and adds its contents
to the compound text context.  

  

For input from a typical text buffer, just specify COMP\_PRESERVE\_LINES.  For
input from a typical character text file, specify COMP\_FROM\_FILE |
COMP\_PRESERVE\_LINES | COMP\_PARA\_BLANK\_LINE.    

  

If the COMP\_PRESERVE\_LINES flag is set, CompoundTextAddTextExt preserves the
line breaks it finds in the input text. For each line delimiter found in the
input, CompoundTextAddTextExt inserts a hard line break (a zero byte) in the
CDTEXT record. Set COMP\_PRESERVE\_LINES if your input text contains lines that
should remain separate after input into Domino or Notes. Clear
COMP\_PRESERVE\_LINES if you do not need to perserve the line formatting of your
input text.  

  

The flags COMP\_PARA\_LINE and COMP\_PARA\_BLANK\_LINE control when
CompoundTextAddTextExt emits a new paragraph.  A new paragraph in the compound
text context consists of a CDPARAGRAPH record followed by a CDPABREFERENCE
record.  

  

The flag COMP\_PARA\_LINE causes CompoundTextAddTextExt to emit a new paragraph
for each line delimiter it encounters in the input.  

  

The flag COMP\_PARA\_BLANK\_LINE causes CompoundTextAddTextExt to emit a new
paragraph only when it encounters a line containing just a line delimiter.   

  

If neither COMP\_PARA\_LINE nor COMP\_PARA\_BLANK\_LINE are set,
CompoundTextAddTextExt will break large amounts of input into paragraphs of
approximately 10K of text each.   

  

Note: it is redundant to specify both COMP\_PARA\_LINE and COMP\_PARA\_BLANK\_LINE.  

  

Note: if both COMP\_PARA\_LINE and COMP\_PRESERVE\_LINES are specified,
CompoundTextAddTextExt ignores COMP\_PRESERVE\_LINES.


 


CompoundTextAddTextExt
can add up to 5 megabytes of text to a rich text item.  The input text from
either a memory buffer or a file is automatically divided into Domino items
that are approximately 30 kilobytes in size.  If COMP\_PARA\_LINE is not
specified, or if COMP\_PARA\_BLANK\_LINE is specified and no blank lines are
found, a paragraph is automatically emitted after every 10 kilobytes of text.


 


The flag
COMP\_SERVER\_HINT\_FOLLOWS is used with the compound text document link functions
to provide a "hint" string containing a server name following the
doclink record.  The server name follows the comment string.  If this flag is
set, the pszComment parameter points to two consecutive NUL-terminated
strings:  the comment string, the NUL terminator ('\0'), the server name, and a
second NUL terminator.


 **See Also :**


**[CompoundTextAddDocLink](CompoundTextAddDocLink.md)**


**[CompoundTextAddTextExt](CompoundTextAddTextExt.md)**



----------------------------------------------------------------------------------------------------------


 





