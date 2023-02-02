##### Function : OLE
##### NSFNoteExtractOLE2Object - Create a copy of an OLE2 object structured storage file, serialized to an On-disk file.
---
##### #include <nsfole.h>
STATUS LNPUBLIC **NSFNoteExtractOLE2Object(**

	NOTEHANDLE  hNote,
	char *pszObjectName,
	char *pszFileName,
	ENCRYPTION_KEY *pEncryptionKey,
	BOOL  fOverwrite,
	DWORD  dwFlags);
**Description :**
This is the OLE2 structured storage file that Domino uses to contain a single 
OLE object.  The resulting structured storage file contains the "normal" OLE 
streams and a single child sub-storage for the OLE object.  The child storage 
is named by it's OLE ProgID which is what Domino uses to locate the storage 
when loading the object.
**Parameters :**
Input :
hNote  -  Note handle of open note.

pszObjectName  -  Name of the OLE $FILE object which is the "master" extendable file object ("ext***") in the set of $FILE objects that comprise this OLE object.

pszFileName  -  The file name, including path, into which the Storage file will be dumped.

pEncryptionKey  -  The Note's bulk data encryption key, acquired from NSFNoteDecrypt.

fOverwrite  -  TRUE to overwrite the file, if it already exists.

dwFlags  -  Additional flags, unused at this time, must be 0.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_NSF_NOT_SUPPORTED - This function is not supported on this platform.  In Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on Windows 32-bit platforms only.  As of Release 5.0.8, this function is supported on all Domino and Notes platforms.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.


**See Also :**
[NSFNoteAttachOLE2Object](D:/md_files/NSFNoteAttachOLE2Object.md)
[NSFNoteDeleteOLE2Object](D:/md_files/NSFNoteDeleteOLE2Object.md)
---
