




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



**NSFNoteDecrypt** **- Decrypts
(unseals) a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteDecrypt(**  

      HANDLE  hNote,  

      WORD  DecryptFlags,  

      ENCRYPTION\_KEY far \*retKeyForAttachments**);**



**Description :**



This
function decrypts an encrypted note, using the appropriate encryption key
stored in the user's ID file.  If the user does not have the appropriate
encryption key to decrypt the note, an error is returned.    

  

File attachments are not decrypted.  However, this function can optionally
return an ENCRYPTION\_KEY structure pointer which can then be used in
NSFNoteExtractFile or NSFNoteExtractFileExt to decrypt a file attachment.


  

    **Note: NSFNoteDecrypt should be deprecated from Notes/Domino 8.0.1. The preferred
function to use in their place is NSFNoteCipherDecrypt.**



**Parameters :**



Input :  

hNote  -  Handle to the open note.  

  

DecryptFlags  -  Use DECRYPT\_ATTACHMENTS\_IN\_PLACE if this note is to be
encrypted again with NSFNoteCopyAndEncrypt.  Otherwise use 0.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully decrypted.  

ERR\_NOTE\_NOT\_SEALED - The note is not encrypted.  

ERR\_BSAFE\_UNSUPPORTED\_CRYPTO\_OP - One possible cause of this error is when the
note is encrypted using an encryption key type that is supported only in N/D
8.01 and later (e.g. AES).  The function cannot write the retKeyForAttachments
output parameter in such cases because an ENCRYPTION\_KEY data structure is not
sufficient to describe that key type.  A work-around is to continue to use this
function but specify the DECRYPT\_ATTACHMENTS\_IN\_PLACE flag; this means any
attachments will be decrypted immediately, and thus the retKeyForAttachments
argument should be unnecessary.  The recommended action is to modify the code
to use NSFNoteCipherDecrypt instead, which supports all key types.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

  

retKeyForAttachments  -  Optional.  Pointer to a returned ENCRYPTION\_KEY
structure.  This pointer may then be passed in to NSFNoteExtractFile or
NSFNoteExtractFileExt to decrypt a file attachment.  Use NULL if this
information is not needed.  

  




 **See Also :**


**[NSFNoteCopyAndEncrypt](NSFNoteCopyAndEncrypt.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**


**[NSFNoteExtractFileExt](NSFNoteExtractFileExt.md)**



----------------------------------------------------------------------------------------------------------


 





