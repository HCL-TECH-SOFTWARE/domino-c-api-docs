




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



**NSFNoteLinkFromText** **- Convert
tagged text to NOTELINK.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteLinkFromText(**  

      DHANDLE  hLinkText,  

      WORD  LinkTextLength,  

      NOTELINK far \*NoteLink,  

      char far \*ServerHint,  

      char far \*LinkText,  

      WORD  MaxLinkText,  

      DWORD far \*retFlags**);**



**Description :**



Converts a
link to a note stored as tagged text to a NOTELINK structure.  The text
containing the link must be stored in a Domino memory object.  The tagged text
format for a note link is:


 


Link Title
String


<NDL>  

<REPLICA>85250123:006E4567</REPLICA>  

<VIEW>OF85258901:00682345-ON8525ABCD:0065EF01</VIEW>  

<NOTE>OF4E851234:A91A5678-ON85259ABC:004BDEF0</NOTE>  

<HINT>CN=Ann/O=Iris</HINT>  

<REM>Database 'Sample Database', View 'Example View', Document 'Title of
Note'</REM>  

<FLAGS ADDTEMPORARY=1 NOREPLSEARCH=1>  

</NDL>


 


 


 


**Parameters :**



Input :  

hLinkText  -  Handle to Notes memory object containing the link text.  

  

LinkTextLength  -  Size, in bytes, of the link text.  

  

MaxLinkText  -  Maximum number of bytes to copy to the LinkText address.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - Conversion successful.  

ERR\_LINK\_FORMAT - Format of the link text is invalid.  

  

  

NoteLink  -  The NOTELINK structure is written to this address.  

  

ServerHint  -  The string in the <HINT> tag is copied to this address.  

  

LinkText  -  The string in the <REM> tag is copied to this address.  

  

retFlags  -  Link flag bits are stored at this address (see the entry for
LINKFLAG\_xxx).  

  




 **See Also :**


**[LINKFLAG\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/B8E44CC9387F8EF3852562A700582647)**


**[NOTELINK](NOTELINK.md)**


**[NSFNoteLinkToText](NSFNoteLinkToText.md)**



----------------------------------------------------------------------------------------------------------


 





