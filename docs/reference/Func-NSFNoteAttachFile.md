##### Function : File Attachment
##### NSFNoteAttachFile - Attaches a disk file to a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteAttachFile(**

	NOTEHANDLE  note_handle,
	const char far *item_name,
	WORD  item_name_length,
	const char far *file_name,
	const char far *orig_path_name,
	WORD  encoding_type);
**Description :**
Attaches a disk file to a note.  To accomplish this, the function creates an 
item of TYPE_OBJECT, sub-category OBJECT_FILE, whose ITEM_xxx flag(s) are set 
to ITEM_SIGN | ITEM_SEAL.  The item that is built by NSFNoteAttachFile contains 
all relevant file information and the compressed file itself.  Since the Item 
APIs offer no means of dealing with signed, sealed, or compressed item values, 
the File Attachment API NSFNoteDetachFile must be used exclusively to access 
these items.
**Parameters :**
Input :
note_handle  -  Handle of note to which the disk file will be attached.

item_name  -  Name of item in note into which file is to be placed.  This is normally set  to ITEM_NAME_ATTACHMENT.

item_name_length  -  Length of item_name.

file_name  -  The address of a null-terminated file name string containing the fully qualified file path specification for file being attached.

orig_path_name  -  The address of a null-terminated string containing a filename that will be stored internally with the attachment, displayed with the atttachment icon when the document is viewed in the Notes user interface, and subsequently used when selecting which attachment to Extract or Detach  and what path to create for an Extracted file.  Note that these operations may be carried out  both from the workstation application Attachments dialog box and programmatically, so try to choose meaningful filenames as opposed to attach.001, attach002, etc., whenever possible.  If attaching mulitiple files that have the same filename but different content to a single document, make sure this variable is unique in each call to NSFNoteAttachFile().

encoding_type  -  This WORD contains a COMPRESS_xxx value that specifies the compression method used to store the file in the note. The compression flag value may optionally be bitwise OR'd with a HOST_xxx value to define the type of file being attached.  In most cases a HOST_xxx value will not be specified, and Domino or Notes will set the file type automatically.  See the chapter on embedding OLE objects in the User Guide for more information on specifying the HOST_xxx of a file attachment.  This value also may optionally be bitwise OR'd with an EFLAGS_xxx value that specifies filename options.  This value also may optionally be bitwise OR'd with an NTATT_xxx value that specifies file types of a file attachment.

Output :
(routine)  -  Return status from this call: 

NOERROR -  A successful call. 

ERR_xxx - Errors returned by lower level functions.  Use the code in a call to OSLoadString and display/log the error for the user.


**Sample Usage :**
```
error = NSFNoteAttachFile (hMessage,
    ITEM_NAME_ATTACHMENT,   
    strlen(ITEM_NAME_ATTACHMENT), 
    filename, pathname, COMPRESS_HUFF);
```
**See Also :**
[COMPRESS_xxx](D:/md_files/COMPRESS_xxx.md)
[HOST_xxx](D:/md_files/HOST_xxx.md)
[EFLAGS_xxx](D:/md_files/EFLAGS_xxx.md)
[NTATT_xxx](D:/md_files/NTATT_xxx.md)
[NSFNoteExtractFile](D:/md_files/NSFNoteExtractFile.md)
[NSFNoteExtractFileExt](D:/md_files/NSFNoteExtractFileExt.md)
---
