##### Function : Note
##### NSFNoteSignExt - Sign all or specific items in a note and append a signature item to the note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteSignExt(

	NOTEHANDLE  hNote,
	const char far *SignatureItemName,
	WORD  ItemCount,
	DHANDLE  hItemIDs);
```
**Description :**

Use this function to sign one section of a document. This function works just 
like NSFNoteSign, but provides the added flexibility needed to sign just the 
fields that reside in a section of a document, and to give the signature item 
the appropriate name. Use NSFNoteSign() to sign the entire document. 

NSFNoteSignExt generates a signature item with the specified name and appends 
this signature item to the note. A signature item has data type TYPE_SIGNATURE 
and item flags ITEM_SEAL. The data value of the signature item is a digest of 
the data stored in items in the note, signed with the user's private key.

To sign all the fields that reside in one section of a note, you need the name 
of the section and the BLOCKIDs of all the items in the section. Format a 
signature item name as a zero-terminated ASCI string of the form 
$Sig_<sectionname>.  Allocate a block of memory in which to store an array of 
item BLOCKIDs.  Initialize this array with the BLOCKIDs of all the items in the 
section.  Then call NSFNoteSignExt specifying the handle to the note, the 
signature item name, the count of items in the section, and the handle to the 
block of memory containing the array of item BLOCKIDs.  NSFNoteSignExt will  
create a digital signature from the specified items and append this digital 
signature item to the note.

If the document to be signed is encrypted, this function will attempt to 
decrypt the document in order to generate a valid signature.  If you want the 
document to be signed and encrypted, you must sign the document  before using 
NSFNoteCopyAndEncrypt.

Note:  When the Notes user interface opens a note, it always uses the 
OPEN_EXPAND option to promote items of type number to number list, and items of 
type text to text list.  In order for a signature created or verified through 
this API call to work correctly with the Notes user interface, the OPEN_EXPAND 
option must be used when the note is opened.

**Parameters :**
Input :
hNote  -  The handle of an open note.

SignatureItemName  -  A zero-terminated LMBCS string specifying the name of the signature item to append. Specify NULL to append a signature item with the name $Signature (ITEM_NAME_NOTE_SIGNATURE). To sign a section, specify a name with the format $Sig_<sectionname>, where <sectionname> is the name of a section to sign.

ItemCount  -  The number of BLOCKIDs in the array specified by hItemIDs. Specify MAXWORD to sign all the signable items in the note.

hItemIDs  -  Handle to memory block containing an array of item BLOCKIDs. To sign a section, the array must contain the item BLOCKIDs of all items in the section. To sign the entire document, specify NULLHANDLE .

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**Sample Usage :**
```
STATUS error;
NOTEHANDLE  hNote;
char *szSectionName;
char szSigItemName[ITEM_NAME_MAX+1];
char *aszItemNames[NUM_ITEMS_IN_SECTION];
DHANDLE hItemBLOCKIDs;
BLOCKID *pItemBLOCKID;
int i;
WORD    wType;
BLOCKID bhValue;
DWORD   dwLength;


/* hNote is the handle to an open document that includes a section. The
   name of this section is specified in szSectionName. There are
   NUM_ITEMS_IN_SECTION items in this section. The array aszItemNames[]
   contains the field names of all the items in this section.
   First, format a name for the signature item.
*/

strcpy(szSigItemName, ITEM_NAME_NOTE_SIG_PREFIX);
strncat(szSigItemName, szSectionName, ITEM_NAME_MAX);

/* Allocate and initialize an array of BLOCKIDs of items in the section */

if (error = OSMemAlloc(0, NUM_ITEMS_IN_SECTION * sizeof(BLOCKID),
                       &hItemBLOCKIDs))
{
    return(error);
}

pItemBLOCKIDs = (BLOCKID*)OSLockObject(hItemBLOCKIDs);

for (i = 0; i < NUM_ITEMS_IN_SECTION; i++)
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

/* sign the items in the section */

if (error = NSFNoteSignExt( hNote,
                            szSigItemName,
                            NUM_ITEMS_IN_SECTION,
                            hItemBLOCKIDs ))
{
    OSMemFree(hItemBLOCKIDs);
    return(error);
}

OSMemFree(hItemBLOCKIDs);
```
**See Also :**
[NSFNoteSign](/reference/Func/NSFNoteSign)
[NSFNoteVerifySignature](/reference/Func/NSFNoteVerifySignature)
[NSFNoteUnsign](/reference/Func/NSFNoteUnsign)
---
