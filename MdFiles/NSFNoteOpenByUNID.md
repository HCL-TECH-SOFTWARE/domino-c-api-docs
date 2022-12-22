




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




 


**Function : Note**



**NSFNoteOpenByUNID** **- Opens a
note, given the note's Universal Note ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteOpenByUNID(**  

      DBHANDLE  hDB,  

      UNID far \*pUNID,  

      WORD  flags,  

      NOTEHANDLE far \*rethNote**);**



**Description :**



This
function takes the Universal Note ID and reads the note into memory and returns
a handle to the in-memory copy. This function only supports the set of 16-bit
WORD options described in the entry OPEN\_xxx.  

  

Use NSFNoteClose to close the note handle and deallocate the memory associated
with it.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note.  

  

pUNID  -  The Universal Note ID.  

  

flags  -   Flags that control the manner in which the note is opened. This, in
turn, controls what information about the note is available to you and how it
is structured. The flags are defined in OPEN\_xxx (note) and may be or'ed
together to combine functionality.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully opened the note.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

rethNote  -  The address in which the handle of the opened note is returned.  

  




 **See Also :**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[OPEN\_xxx (note)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B660055DC1F)**



----------------------------------------------------------------------------------------------------------


 





