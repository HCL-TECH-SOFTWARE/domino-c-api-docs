




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



**Function : Security**



**NSFNoteSignExt3** **- Sign all
or specific items in a note and append a signature item to the note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteSignExt3(**  

      NOTEHANDLE  hNote,  

      KFHANDLE  hKFC,  

      const char far \*SignatureItemName,  

      WORD  ItemCount,  

      DHANDLE  hItemIDs,  

      DWORD  Flags,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This
function works just like NSFNoteSignExt - it allows you to sign just the fields
that reside in a section of a document, and to give the signature item the
appropriate name.  In addition, this function allows you to pass a flag to
determine how MIME parts will be signed.  This function requires  you to
specify a handle to a specific ID file.  

  

NSFNoteSignExt3 generates a signature item with the specified name and appends
this signature item to the note. A signature item has data type TYPE\_SIGNATURE
and item flags ITEM\_SEAL. The data value of the signature item is a digest of
the data stored in items in the note, signed with the user's private key.  

  

To sign all the fields that reside in one section of a note, you need the name
of the section and the BLOCKIDs of all the items in the section. Format a
signature item name as a zero-terminated ASCI string of the form
$Sig\_<sectionname>.  Allocate a block of memory in which to store an
array of item BLOCKIDs.  Initialize this array with the BLOCKIDs of all the
items in the section.  Then call NSFNoteSignExt3 specifying the handle to the
note, the signature item name, the count of items in the section, and the
handle to the block of memory containing the array of item BLOCKIDs. 
NSFNoteSignExt3 will  create a digital signature from the specified items and
append this digital signature item to the note.


 


 If the note
has MIME parts then it will be SMIME signed.  If not, or the Flags parameter is
set to allow Notes signature on MIME parts, then it will be Notes signed.


 


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

hNote  -  Handle to an open note that is to be signed.  

  

hKFC  -  Handle to an ID file.  Pass NULL for current user's ID.  

  

SignatureItemName  -  A zero-terminated LMBCS string specifying the name of the
signature item to append. Specify NULL to append a signature item with the name
$Signature (ITEM\_NAME\_NOTE\_SIGNATURE). To sign a section, specify a name with
the format $Sig\_<sectionname>, where <sectionname> is the name of a
section to sign.  

  

  

ItemCount  -  The number of BLOCKIDs in the array specified by hItemIDs.
Specify MAXWORD to sign all the signable items in the note.  

  

hItemIDs  -  Handle to memory block containing an array of item BLOCKIDs. To
sign a section, the array must contain the item BLOCKIDs of all items in the
section. To sign the entire document, specify NULLHANDLE .  

  

Flags  -   If 0, and the note has MIME parts, then it will be SMIME signed.  If
not or the Flags parameter is set to allow Notes signature on MIME parts then
it will be Notes signed.  See SIGN\_NOTES\_IF\_MIME\_PRESENT.  

  

Reserved  -  Reserved, should be 0.  

  

pReserved  -  Reserved, should be NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **See Also :**


**[SECKFMOpen](SECKFMOpen.md)**


**[SIGN\_NOTES\_IF\_MIME\_PRESENT](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/215011A1D2AE9B9E85256DD50057CD30)**



----------------------------------------------------------------------------------------------------------


 





