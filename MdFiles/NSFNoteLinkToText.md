




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




**Initial Release 4.0**



**Function : HTML**



**NSFNoteLinkToText** **- Convert
NOTELINK to tagged text.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteLinkToText(**  

      char far \*Title,  

      NOTELINK far \*NoteLink,  

      char far \*ServerHint,  

      char far \*LinkText,  

      DHANDLE far \*phLinkText,  

      WORD far \*pLinkTextLength,  

      DWORD  Flags**);**



**Description :**



Converts a
NOTELINK structure to tagged text note link format.  The format of the tagged
text is described in the entry for NSFNoteLinkFromText().  A Domino memory
object is allocated to store the tagged text;  the caller is responsible for
freeing this memory object.


 


**Parameters :**



Input :  

Title  -  Title string for the note link.  

  

NoteLink  -  NOTELINK structure.  

  

ServerHint  -  Text to be written to the <HINT> tag.  

  

LinkText  -  Descriptive text to be written to the <REM> tag.  

  

Flags  -  Note link option flags (see the entry for LINKFLAG\_xxx).  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - Conversion successful.  

  

  

phLinkText  -  The handle to the memory object containing the tagged text note
link is stored at this address.  

  

pLinkTextLength  -  The size of the tagged text note link, in bytes, is written
to this address.  

  




 **See Also :**


**[LINKFLAG\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/B8E44CC9387F8EF3852562A700582647)**


**[NOTELINK](NOTELINK.md)**


**[NSFNoteLinkFromText](NSFNoteLinkFromText.md)**



----------------------------------------------------------------------------------------------------------


 





