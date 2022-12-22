




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



**NSFNoteSign** **- Appends a
digital signature to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteSign(**  

      NOTEHANDLE  hNote**);**



**Description :**



This
function signs a document by creating a unique electronic signature and
appending this signature to the note.   A signature constitutes proof of the
user's identity and serves to assure the reader that the user was the real
author of the document.   

  

The signature is derived from the User ID. A signature item has data type
TYPE\_SIGNATURE and item flags ITEM\_SEAL. The data value of the signature item
is a digest of the data stored in items in the note, signed with the user's
private key.   

  

NSFNoteSign signs entire document. It creates a digest of all the items in the
note, and appends a signature item with field name $Signature
(ITEM\_NAME\_NOTE\_SIGNATURE).  Use NSFNoteSignExt() to sign a section of a note.


 


If the
document to be signed is encrypted, this function will attempt to decrypt the
document in order to generate a valid signature.  If you want the document to
be signed and encrypted, you must sign the document  before using
NSFNoteCopyAndEncrypt.


 


**Note:**  When the
Notes user interface opens a note, it always uses the OPEN\_EXPAND option to
promote items of type number to number list, and items of type text to text
list.  In order for a signature created or verified through this API call to
work correctly with the Notes user interface, the OPEN\_EXPAND option must be
used when the note is opened.


 


**Parameters :**



Input :  

hNote  -  The handle of an open note.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **See Also :**


**[NSFNoteSignExt](NSFNoteSignExt.md)**


**[NSFNoteUnsign](NSFNoteUnsign.md)**


**[NSFNoteVerifySignature](NSFNoteVerifySignature.md)**


**[OPEN\_xxx (note)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B660055DC1F)**



----------------------------------------------------------------------------------------------------------


 





