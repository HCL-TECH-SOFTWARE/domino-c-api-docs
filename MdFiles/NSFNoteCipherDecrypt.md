




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




**Initial Release 8.0.1**



**Function : encryption**



**NSFNoteCipherDecrypt** **- Decrypts
(unseals) a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCipherDecrypt(**  

      NOTEHANDLE  hNote,  

      KFHANDLE  hKFC,  

      DWORD  DecryptFlags,  

      CIPHERHANDLE far \*rethCipherForAttachments,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This
function decrypts an encrypted note, using the appropriate encryption key
stored in the user's ID file.  If the user does not have the appropriate
encryption key to decrypt the note, an error is returned.  


 


      This
function supports new cryptographic keys and algorithms introduced in Release
8.0.1 as well as any from releases prior to 8.0.1.  Thus it is preferred over
the functions NSFNoteDecrypt and NSFNoteDecryptExt2 in cases where their
ENCRYPTION\_KEY argument is specified and is used in subsequent operations.  

  

By default, file attachments and objects are not decrypted, but a flag may be
specified to do so as part of this function (see below).  Alternatively, this
function can optionally return a CIPHERHANDLE which can then be used as input
to other functions to decrypt attachments or objects.


 


 


**Parameters :**



Input :  

hNote  -  Handle to the open note.  

  

hKFC  -  Handle to an ID file.  Pass NULLKFHANDLE for current user's ID.  

  

DecryptFlags  -  Use DECRYPT\_ATTACHMENTS\_IN\_PLACE to decrypt attachments as
part of this operation, or if this note is to be encrypted again with
NSFNoteCopyAndEncrypt.  See DECRYPT\_xxx.  Otherwise use 0.  

  

rethCipherForAttachments  -  If non-NULL on input, the referenced CIPHERHANDLE
is assumed to be an existing handle obtained from a previous call, and it is
freed with NSFCipherDestroy before overwriting with new data; otherwise, the
CIPHERHANDLE must be equal to NULLCIPHERHANDLE on input.  

  

Reserved  -  Reserved, must be 0.  

  

pReserved  -  Reserved, must be NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully decrypted.  

ERR\_NOTE\_NOT\_SEALED - The note is not encrypted.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

rethCipherForAttachments  -  Optional.  Pointer to a returned CIPHERHANDLE. 
The CIPHERHANDLE may then be passed in to NSFNoteCipherExtractFile or
NSFNoteCipherExtractWithCallback to decrypt a file attachment.  Use NULL if
this information is not needed.  When done with the CIPHERHANDLE, your code
must call NSFCipherDestroy to release memory and resources associated with it. 
The returned CIPHERHANDLE will always be equal to NULLCIPHERHANDLE if the
function returns any error status other than NOERROR.  

  




 **Sample Usage :**


NOTEID
note1\_id, note2\_id;


STATUS
error = NOERROR;


CIPHERHANDLE
rethCipherAttachments;


error
= NSFNoteCreate(hDb, &hnote1);


error
= NSFNoteCopyAndEncrypt(hnote1, ENCRYPT\_WITH\_USER\_PUBLIC\_KEY, &hnote2);


 


error
= OSMemoryAllocate(0, MAXONESEGSIZE, &rethCipherAttachments);


error
= NSFNoteCipherDecrypt(hnote2, NULLKFHANDLE, 0, &rethCipherAttachments, 0,
NULL);


 **See Also :**


**[NSFNoteCipherExtractFile](NSFNoteCipherExtractFile.md)**


**[NSFNoteCopyAndEncrypt](NSFNoteCopyAndEncrypt.md)**



----------------------------------------------------------------------------------------------------------


 





