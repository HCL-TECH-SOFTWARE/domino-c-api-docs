




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




**Initial Release 7.0**



**Function : Note**



**NSFNoteCopyAndEncryptExt2** **- Copies
and encrypts (seals) a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCopyAndEncryptExt2(**  

      NOTEHANDLE  hSrcNote,  

      KFHANDLE  hKFC,  

      WORD  EncryptFlags,  

      NOTEHANDLE far \*rethDstNote,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This
function copies and encrypts (seals) the encryption enabled fields in a note
(including the note's file objects), using a handle to an ID file.


 


NSFNoteCopyAndEncryptExt2
can encrypt a note in several ways -- by using the Domino public key of the
caller, by using specified secret encryption keys stored in the caller's ID, or
by using the Domino public keys of specified users, if the note does not have
any mime parts.


 


NSFNoteCopyAndEncryptExt2
decides which type of encryption to do based upon the setting of the flag
passed to it in its EncryptFlags argument.  If the ENCRYPT\_WITH\_USER\_PUBLIC\_KEY
flag is set, it uses the caller's public ID to encrypt the note.  In this case,
only the user who encodes the note can decrypt it.  This feature allows an
individual to protect information from anyone else.


 


If, instead,
the ENCRYPT\_WITH\_USER\_PUBLIC\_KEY flag is not set, then the function expects the
note to contain  a field named ITEM\_NAME\_NOTE\_SEALNAMES ( defined to be
"SecretEncryptionKeys" in stdnames.h), a field named
ITEM\_NAME\_NOTE\_SEALUSERS  (defined to be "PublicEncryptionKeys" in
stdnames.h), or both.  Each field is either a TYPE\_TEXT or TYPE\_TEXT\_LIST field.


 


ITEM\_NAME\_NOTE\_SEALNAMES
contains the name(s) of the secret encryption keys in the calling user's ID to
be used to encrypt the note.  This feature is intended to allow a group to
encrypt some of the notes in a single database in a way that only they can
decrypt them -- they must share the secret encryption keys among themselves
first for this to work.


 


ITEM\_NAME\_NOTE\_SEALUSERS
contains the name(s) of  users, in canonical format.  The note will be
encrypted with each user's Domino public key.  The user can then decrypt the
note with the private key in the user's ID.  This feature provides a way to
encrypt documents, such as mail documents, for another user.


 


The note
must contain at least one encryption enabled item (an item with the ITEM\_SEAL
flag set) in order to be encrypted.  Use NSFNoteClose to close the note handle
and deallocate the memory associated with it.


 


If the note
has mime parts and flag ENCRYPT\_SMIME\_IF\_MIME\_PRESENT is set, then it is SMIME
encrypted.


 


If the
document is to be signed as well as encrypted, you must sign the document
NSFNoteSignExt3) before using NSFNoteCopyAndEncrypt.Ext2


 


**Parameters :**



Input :  

hSrcNote  -  Handle to the open note.  

  

hKFC  -  Handle to an ID file.  Pass NULL for current user's ID.  

  

EncryptFlags  -  Optional.  Use 0 for the note to be encrypted with a personal
key.  An ITEM\_NAME\_NOTE\_SEALNAMES item containing the name of the personal key
must have been appended to the note previously.  See ENCRYPT\_xxx for other
options.  

  

Reserved  -  Reserved, should be 0.  

  

pReserved  -  Reserved, should be NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully copied and encrypted.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

rethDstNote  -  Pointer to the handle of the returned copy of the note.  This
returned copy is the encrypted version of the note.  

  




 **See Also :**


**[ENCRYPT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/07234B7BAD25436485256237004FFCD5)**


**[NSFNoteDecrypt](NSFNoteDecrypt.md)**


**[SECKFMOpen](SECKFMOpen.md)**



----------------------------------------------------------------------------------------------------------


 





