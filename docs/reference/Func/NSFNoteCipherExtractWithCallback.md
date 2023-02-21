##### Function : encryption
##### NSFNoteCipherExtractWithCallback - Extract a file with a user defined call back function.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteCipherExtractWithCallback(

	NOTEHANDLE  hNote,
	BLOCKID  bhItem,
	DWORD  ExtractFlags,
	CIPHERHANDLE  hDecryptionCipher,
	NOTEEXTRACTCALLBACK  pNoteExtractCallback,
	void far *pParam,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This function allows flexibility with file attachments.  It may be desirable to 
read through file attachment data without having to save the file to disk.  The 
user defined call back function will be called however many times necessary 
with a pointer to the file data and the number of bytes returned.  The user has 
the option with the call back function to do what is desired with the 
attachment data.
	
	This function supports new cryptographic keys and algorithms introduced 
in Release 8.0.1 as well as any from releases prior to 8.0.1.  Thus it is 
preferred over the function NSFNoteExtractWithCallback in cases where its 
ENCRYPTION_KEY argument is non-NULL.


**Parameters :**
Input :
hNote  -  Handle of note with a file attachment.

bhItem  -  BLOCKID of the attachment item from which file is to be extracted.  The BLOCKID can be easily obtained by item name using NSFItemInfo.

ExtractFlags  -  The possible values for the ExtractFlags are defined by the NTEXT_xxx symbols.

hDecryptionCipher  -  Use NULLCIPHERHANDLE if the attachment is not encrypted, or if it has already been decrypted by using a note decryption function with the DECRYPT_ATTACHMENTS_IN_PLACE flag.  Otherwise, use a CIPHERHANDLE returned by NSFNoteCipherDecrypt.

pNoteExtractCallback  -  A pointer to the user defined Call back function.  

pParam  -  user defined parameter passed to the user defined call back routine NOTEEXTRACTWITHCALLBACK.  This data can be a means for keeping track of information during the process of extracting an attached file.  For example a structure can be defined that can keep track of the amount of data extracted and information on the extracted file if the extracted data is to be written to a file.

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
STATUS LNCALLBACK ExtractwithCallback(const BYTE* byte, DWORD length, void far* 
pParam);

error = NSFDbOpen(localdb, &hDb);
error = NSFNoteCreate(hDb, &hnote);

#ifdef W32
	_getcwd(filepath, _MAX_PATH);
#ifdef UNIX
	strcpy(filepath, getenv("PWD"));
#endif
#endif
	
strcat(filepath, "\\readme.txt");
	
error = NSFNoteAttachFile(hnote, ITEM_NAME_ATTACHMENT,
	 strlen(ITEM_NAME_ATTACHMENT), filepath ,"readme.txt",COMPRESS_HUFF);
error = NSFNoteUpdate(hnote, UPDATE_FORCE);
error = NSFNoteHasObjects(hnote, &retbid);

error = NSFNoteExtractWithCallback(hnote, retbid, NULL, 0,ExtractwithCallback, 
(void*)&totallen);
&rethCipherAttachments);
tus = EXIT_FAILURE;

STATUS LNCALLBACK ExtractwithCallback(const BYTE* byte, DWORD length, void far* 
pParam)
{
	int totallen = *(int *)pParam;
	char *localstr = (char*)byte;
	if (localstr != NULL) {
	 fprintf(flog, "current content: %s\n", localstr);
	 fprintf(flog, "current length : %d\n", length);
	 totallen += length;
	 fprintf(flog, "total length : %d\n", totallen);
	 memset(fileContent, '\0', sizeof(fileContent));
	 strncpy(fileContent, localstr, length);
//  strcat(fileContent, '\0');
	}
	
	return NOERROR;
}
```
**See Also :**
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
---
