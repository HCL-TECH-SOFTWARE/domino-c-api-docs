##### Function : File Attachment
##### NSFNoteExtractWithCallback - Extract a file with a user defined call back function.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteExtractWithCallback(

	NOTEHANDLE  hNote,
	BLOCKID  bhItem,
	ENCRYPTION_KEY far *DecryptionKey,
	WORD  wFlags,
	NOTEEXTRACTCALLBACK  pNoteExtractCallback,
	void far *pParam);
```
**Description :**

This function allows flexibility with file attachments.  It may be desirable to 
read through file attachment data without having to save the file to disk.  The 
user defined call back function will be called however many times necessary 
with a pointer to the file data and the number of bytes returned.  The user has 
the option with the call back function to do what is desired with the 
attachment data.

   Note: NSFNoteExtractWithCallback should be deprecated from Notes/Domino 
8.0.1. The preferred function to use in their place is NSFNoteCipherDecrypt.

**Parameters :**
Input :
hNote  -  Handle of note with a file attachment.

bhItem  -  BLOCKID of the attachment item from which file is to be extracted.  The BLOCKID can be easily obtained by item name using NSFItemInfo.

DecryptionKey  -  Use NULL if the attachment is not encrypted.  Otherwise, use a pointer to the ENCRYPTION_KEY structure returned by NSFNoteDecrypt.

wFlags  -  The possible values for the wFlags are defined by the NTEXT_xxx symbol.

pNoteExtractCallback  -  A pointer to the user defined Call back function.  

pParam  -  user defined parameter passed to the user defined call back routine NOTEEXTRACTWITHCALLBACK.  This data can be a means for keeping track of information during the process of extracting an attached file.  For example a structure can be defined that can keep track of the amount of data extracted and information on the extracted file if the extracted data is to be written to a file.

Output :
(routine)  -  Return status from this call includes:

NOERROR - Successfully extracted file.

ERR_ENCODING - Unknown type of compression technique.

ERR_NOEXTRACT_ENCRYPTED - You must supply the decryption key in order to extract this file.

ERR_NOTE_BADATTSIGN - Attachment has been modified or corrupted since signed!

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```
/* Open the note. */

    if (error = NSFNoteOpen (
            *(DBHANDLE*)db_handle,  /* database handle */
            SearchMatch.ID.NoteID,  /* note ID */
            0,                      /* open flags */
            &note_handle))          /* note handle (return) */

        return (error);

/* Look for the File attachment for this note. This function tells us
whether the field is there, and if present, its location (BLOCKID)
within Domino and Notes' memory. Check the return code for "field not found" 
versus
a real error. */

    error = NSFItemInfo (
            note_handle,        /* note handle */
            "$FILE",        /* field we want */
            (WORD)strlen("$FILE"),    /* length of above */
            &bkItem,            /* full field (return) */
            &field_type,        /* field type (return) */
            &field_block,        /* field contents (return) */
            &field_length);        /* field length (return) */

    if (ERR(error) == NOERROR)
        field_found = TRUE;

    if (ERR(error) == ERR_ITEM_NOT_FOUND)
    {
        field_found = FALSE;
        error = NOERROR;
    }

    if (error)
    {
        NSFNoteClose (note_handle);
        return (error);
    }

/* If the RICH_TEXT field is there, do the next few sections of code. */
	memset(&pParam, 0, sizeof(pParam));
    if (field_found)
    {
	/*
        * Call ExtractWithCallback for how ever many times to read through the 
file attachment data
        */ 
	if(error = NSFNoteExtractWithCallback(note_handle, bkItem, NULL, 0, 
ExtractWithCallback, &pParam))
	{
	 NSFNoteClose(note_handle);
	 return(error);
	}
    }
	/* If the $FILE field is not there, print a message. */
    else
        printf ("\n$FILE(file attachment) field not found.\n");

	/* Close the file handle if opened to write data */
	if(pParam.pOutputFile)
	 CloseHandle(pParam.pOutputFile);

/* Close the note. */

    if (error = NSFNoteClose (note_handle))
        return (error);

/* End of subroutine. */

    return (NOERROR);

}

/*
 * User defined call back function to read through the file attachment data.  
In this
 * case the file attachment data will be written to a file.
 */
STATUS LNCALLBACK ExtractWithCallback(const BYTE *bytes, DWORD length, void far 
*pParam)
{
	struct CallBackData *tmpCtx = (struct CallBackData*)pParam;
	DWORD numberWritten = 0;
	STATUS err = NOERROR;

	/* Check to see if first time through */
	if(!tmpCtx->pOutputFile)
	{
	 /* Open the file to write the exported data */
	 tmpCtx->pOutputFile = CreateFile("FileData.Txt",
	  GENERIC_WRITE|GENERIC_READ,FILE_SHARE_READ | FILE_SHARE_WRITE,
	  NULL, CREATE_ALWAYS,FILE_ATTRIBUTE_NORMAL,NULL);
	 if (!tmpCtx->pOutputFile)
	 {
	  printf("Error:  Unable to open output file:%s.\n", "FileData.Txt");
	  goto Exit0;
	 }
	 tmpCtx->totalBytesWritten = 0;
	}
	err = WriteFile(tmpCtx->pOutputFile, bytes, length, &numberWritten, 
NULL);
	if(err == 1)
	 err = NOERROR;
	printf("\nBytesWritten = %s\n",bytes);
	if( numberWritten != length )
	{
	 printf("Error: Did not write specified bytes required %d\n", length );
	 goto Exit0;
	}
	else
	 tmpCtx->totalBytesWritten += numberWritten;

Exit0:
	return(err);
}
```
**See Also :**
[NOTEEXTRACTCALLBACK](/domino-c-api-docs/reference/Data/NOTEEXTRACTCALLBACK)
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
[NSFNoteDecrypt](/domino-c-api-docs/reference/Func/NSFNoteDecrypt)
[NSFNoteDetachFile](/domino-c-api-docs/reference/Func/NSFNoteDetachFile)
[NSFNoteExtractFile](/domino-c-api-docs/reference/Func/NSFNoteExtractFile)
---
