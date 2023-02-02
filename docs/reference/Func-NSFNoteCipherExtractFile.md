##### Function : encryption
##### NSFNoteCipherExtractFile - Extract a file from an item in a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteCipherExtractFile(**

	NOTEHANDLE  hNote,
	BLOCKID  bhItem,
	DWORD  ExtractFlags,
	CIPHERHANDLE  hDecryptionCipher,
	const char far *FileName,
	DWORD  Reserved,
	void *pReserved);
**Description :**
Creates a disk file from the contents of an attached item (referenced by its 
BLOCKID).  The BLOCKID can be easily obtained by item name using NSFItemInfo.  
The FileName parameter specifies the path, file name, and extension of the file 
to be created.  If only a file name and extension are supplied, the file will 
be created in the current working directory.
	
	This function supports new cryptographic keys and algorithms introduced 
in Release 8.0.1 as well as any from releases prior to 8.0.1.  Thus it is 
preferred over the functions NSFNoteExtractFile and NSFNoteExtractFileExt in 
cases where their ENCRYPTION_KEY argument is non-NULL.
**Parameters :**
Input :
hNote  -  Handle of note from which disk file will be extracted.

bhItem  -  BLOCKID of the attachment item from which file is to be extracted.

ExtractFlags  -  The possible values for the ExtractFlags are defined by the NTEXT_xxx symbols.

hDecryptionCipher  -  Use NULLCIPHERHANDLE if the attachment is not encrypted, or if it has already been decrypted by using a note decryption function with the DECRYPT_ATTACHMENTS_IN_PLACE flag.  Otherwise, use a CIPHERHANDLE returned by NSFNoteCipherDecrypt.

FileName  -  A null-terminated file name of the file that will be created.

Reserved  -  Reserved, must be 0.

pReserved  -  Reserved, must be NULL.

Output :
(routine)  -  Return status from this call includes:

NOERROR - Successfully extracted file.

ERR_ENCODING - Unknown type of compression technique.

ERR_NOEXTRACT_ENCRYPTED - You must supply the decryption key in order to extract this file.

ERR_NOTE_BADATTSIGN - Attachment has been modified or corrupted since signed!

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


**Sample Usage :**
```
STATUS  error; 
DBHANDLE  hDb;
NOTEHANDLE  hnote, hnote1;
char   server[100], serverdb[100];
BLOCKID retbid;
CIPHERHANDLE rethCipherAttachments;
char filepath[_MAX_PATH];
strcpy(localdb, "extracttest.nsf");

........

error = NSFNoteCreate(hDb, &hnote);
	
#ifdef W32
	_getcwd(filepath, _MAX_PATH);
#ifdef UNIX
	strcpy(filepath, getenv("PWD"));
#endif
#endif 
	 

error = NSFNoteAttachFile(hnote, ITEM_NAME_ATTACHMENT,
	  strlen(ITEM_NAME_ATTACHMENT),filepath,"readme.txt",
	  COMPRESS_HUFF);
error = NSFNoteUpdate(hnote, UPDATE_FORCE);  
error = NSFNoteHasObjects(hnote, &retbid);
error = NSFNoteCopyAndEncrypt(hnote, ENCRYPT_WITH_USER_PUBLIC_KEY, 
	   &hnote1); 
error = OSMemoryAllocate(0, MAXONESEGSIZE, &rethCipherAttachments);
error = NSFNoteCipherDecrypt(hnote1, NULLKFHANDLE, 0, &rethCipherAttachments, 
0, NULL);
error = NSFNoteCipherExtractFile(hnote1, retbid, 0, rethCipherAttachments, 
"out.txt",0, NULL);
error = NSFCipherDestroy(&rethCipherAttachments)) 
remove("out.txt");
NSFNoteClose(hnote);
NSFNoteClose(hnote1);
NSFDbClose(hDb);
```
**See Also :**
[NSFCipherDestroy](D:/md_files/NSFCipherDestroy.md)
[NSFNoteAttachFile](D:/md_files/NSFNoteAttachFile.md)
[NSFNoteCopyAndEncrypt](D:/md_files/NSFNoteCopyAndEncrypt.md)
---
