




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Function : Item Conversion**



**ConvertItemToCompositeExt** **- Converts
text item to composite item, allowing use of NLS\_INFO structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



STATUS
LNPUBLIC **ConvertItemToCompositeExt(**  

      BLOCKID  ItemValue,  

      DWORD  ItemValueLength,  

      FONTID  CompositeFont,  

      char far \*LineDelimiter,  

      WORD  ParaDelimiterFlags,  

      DHANDLE far \*rethBuffer,  

      DWORD far \*retBufferLength,  

      NLS\_PINFO  pInfo,  

      int  CDFileFD,  

      BOOL  fAppendToFile**);**



**Description :**



This
function converts an item of TYPE\_TEXT to an item of TYPE\_COMPOSITE, allowing
the use of the NLS\_INFO structure.  It takes as input a text item, its length,
a font style, a line delimiter, and a paragraph marker.  The function returns
as output a HANDLE to the composite item and the length of the composite item.  

  

This function is very useful in Import/Export Dynamic Link Libraries (DLLs) and
E-Mail Gateways where plain text or data with imbedded control characters must
be converted to Rich Text.  

  

Note:  Your program is responsible for freeing any memory associated with a
valid handle returned in argument 6.


 


**Parameters :**



Input :  

ItemValue  -  BLOCKID of the TYPE\_TEXT item's value.  

  

ItemValueLength  -  DWORD containing size of item's value.  

  

CompositeFont  -   FONTID to use in conversion.  Structure contains font
typeface, size, color and attribute.  Use DEFAULT\_FONT\_ID for 10 point, plain,
black, Helvetica (also known as Swiss).  These are defined in fontid.h.  

  

LineDelimiter  -   A pointer to a null-terminated string containing
character(s) used to separate input lines.  Common delimeters include
"", "\r\n", and "\n".  The delimiter string is
used to parse each logical line in the input item into "paragraphs",
and then it is stripped from the text stream and never included in the
resulting composite item.  

  

ParaDelimiterFlags  -   WORD describing method to be used for recognizing input
paragraphs and how the resulting paragraphs are to be displayed in Notes. These
are defined in PARADELIM\_xxx.  

  

pInfo  -  A pointer to an NLS\_INFO struct, which contains all of the tables and
attributes of the current character set. The NLS\_INFO struct should have been
initialized by a previous call to OSGetLMBCSCLS().  (NULL if text item already
in the Lotus Multibyte Character Set (LMBCS)).  

  

CDFileFD  -  For internal use only - specify 0 (ZERO).  

  

fAppendToFile  -  For internal use only - specifiy FALSE.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:  

  

NOERROR  - upon successful conversion   

  

ERR\_DATATYPE - if item argument was not TYPE\_TEXT    

  

ERR\_ODS\_TEXT\_TOOBIG - if the item argument was greater than 60K.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that It
is best to use the code in a call to   

  

OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethBuffer  -  Address of a HANDLE in which the handle to the completed
composite buffer will be returned.  Your program is responsible for disposing
of this memory object when it is done via OSMemFree().  

  

retBufferLength  -   Address of a DWORD in which the length of completed
composite buffer will be returned.  

  




 **Sample Usage :**


/\* Convert the Text to
CD and copy ret'd Block to temp CD file   \*/  

  

usError = ConvertItemToCompositeExt(  

               ImpTextBID,   /\* BLOCKID of TEXT ITEM just fabricated\*/  

               dwTextLen,                    /\* Length of TEXT ITEM \*/  

               EditorData->FontID, /\* Use FontID provided by Editor \*/  

               szEOL,             /\* using "\r\n" as line delimiter
\*/  

               ParaDelimiters, /\* using ANYBLANKLINE para delimiter \*/  

               &hCDBuf,            /\* ret'd handle to CD buffer     \*/  

               &dwCDItemLen,         /\* ret'd len of composite item \*/  

               NULL,              

               0,                                 /\* Reserved \*/  

               FALSE);                            /\* Reserved \*/  

  

if (usError)


  goto Exit;  

else  

  wCleanUp |= FREE\_HCDBUF;


 


 **See Also :**


**[EnumCompositeBuffer](EnumCompositeBuffer.md)**


**[ConvertItemToText](ConvertItemToText.md)**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemConvertToText](NSFItemConvertToText.md)**


**[NSFItemConvertValueToText](NSFItemConvertValueToText.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[OSMemFree](OSMemFree.md)**



----------------------------------------------------------------------------------------------------------


 





