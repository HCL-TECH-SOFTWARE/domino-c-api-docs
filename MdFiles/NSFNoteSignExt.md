




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**NSFNoteSignExt** **- Sign all
or specific items in a note and append a signature item to the note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteSignExt(**  

      NOTEHANDLE  hNote,  

      const char far \*SignatureItemName,  

      WORD  ItemCount,  

      DHANDLE  hItemIDs**);**



**Description :**



Use this
function to sign one section of a document. This function works just like
NSFNoteSign, but provides the added flexibility needed to sign just the fields
that reside in a section of a document, and to give the signature item the appropriate
name. Use NSFNoteSign() to sign the entire document.   

  

NSFNoteSignExt generates a signature item with the specified name and appends
this signature item to the note. A signature item has data type TYPE\_SIGNATURE
and item flags ITEM\_SEAL. The data value of the signature item is a digest of
the data stored in items in the note, signed with the user's private key.  

  

To sign all the fields that reside in one section of a note, you need the name
of the section and the BLOCKIDs of all the items in the section. Format a
signature item name as a zero-terminated ASCI string of the form
$Sig\_<sectionname>.  Allocate a block of memory in which to store an
array of item BLOCKIDs.  Initialize this array with the BLOCKIDs of all the
items in the section.  Then call NSFNoteSignExt specifying the handle to the
note, the signature item name, the count of items in the section, and the
handle to the block of memory containing the array of item BLOCKIDs. 
NSFNoteSignExt will  create a digital signature from the specified items and
append this digital signature item to the note.


 


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

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **Sample Usage :**


STATUS error;  

NOTEHANDLE  hNote;  

char \*szSectionName;  

char szSigItemName[ITEM\_NAME\_MAX+1];  

char \*aszItemNames[NUM\_ITEMS\_IN\_SECTION];  

DHANDLE hItemBLOCKIDs;  

BLOCKID \*pItemBLOCKID;  

int i;  

WORD    wType;  

BLOCKID bhValue;  

DWORD   dwLength;  

  

  

/\* hNote is the handle to an open document that includes a section. The  

   name of this section is specified in szSectionName. There are  

   NUM\_ITEMS\_IN\_SECTION items in this section. The array aszItemNames[]  

   contains the field names of all the items in this section.  

   First, format a name for the signature item.  

\*/  

  

strcpy(szSigItemName, ITEM\_NAME\_NOTE\_SIG\_PREFIX);  

strncat(szSigItemName, szSectionName, ITEM\_NAME\_MAX);  

  

/\* Allocate and initialize an array of BLOCKIDs of items in the section \*/  

  

if (error = OSMemAlloc(0, NUM\_ITEMS\_IN\_SECTION \* sizeof(BLOCKID),  

                       &hItemBLOCKIDs))  

{  

    return(error);  

}  

  

pItemBLOCKIDs = (BLOCKID\*)OSLockObject(hItemBLOCKIDs);  

  

for (i = 0; i < NUM\_ITEMS\_IN\_SECTION; i++)  

{  

    if (error = NSFItemInfo(hNote, szSigItemName[i],  

                strlen(szSigItemName[i]), &pItemBLOCKIDs[i],  

                &wType, &bhValue, &dwLength))  

    {  

        OSUnlockObject(hItemBLOCKIDs);  

        OSMemFree(hItemBLOCKIDs);  

        return(error);  

    }  

}  

  

  

OSUnlockObject(hItemBLOCKIDs);  

  

/\* sign the items in the section \*/  

  

if (error = NSFNoteSignExt( hNote,  

                            szSigItemName,  

                            NUM\_ITEMS\_IN\_SECTION,  

                            hItemBLOCKIDs ))  

{  

    OSMemFree(hItemBLOCKIDs);  

    return(error);  

}  

  

OSMemFree(hItemBLOCKIDs);


 **See Also :**


**[NSFNoteSign](NSFNoteSign.md)**


**[NSFNoteVerifySignature](NSFNoteVerifySignature.md)**


**[NSFNoteUnsign](NSFNoteUnsign.md)**



----------------------------------------------------------------------------------------------------------


 





