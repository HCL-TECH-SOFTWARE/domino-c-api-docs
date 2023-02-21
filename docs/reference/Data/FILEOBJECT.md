##### Data Type : File Attachment
##### FILEOBJECT - Structure of a file object item ($FILE).
---
```
#include <nsfdata.h>
```
**Description :**

This is the strucure of a file attachment item.  For each file attached to a 
note, an item with field name "$FILE" (ITEM_NAME_ATTACHMENT) and data type 
TYPE_OBJECT is appended to the note.  The value of this item is a structure of 
type FILEOBJECT.  Note that the data of the attached file is not stored in this 
item. Rather, it is stored in an object identified by the RRV member of the 
OBJECT_DESCRIPTOR.

For normal file attachments, you do not need to access the file attachment item 
directly. Use the functions NSFNoteAttachFile, NSFNoteDetachFile, and 
NSFNoteExtractFile to manipulate file attachments.

If you do need to access items of type FILE_OBJECT directly, and if your API 
program runs on a non-Intel platform such as Unix, then you must convert the 
item data from Domino canonical format to Host format before accessing members 
of the FILEOBJECT structure.

**Sample Usage :**
```
    OBJECT_DESCRIPTOR  *pObject;
    FILEOBJECT         *pFileObject;
    WORD                wFileNameLen;
    BYTE               *pFileNameStart;
    WORD                wHostType;
    CHAR               *szHostType;
    WORD                wCompress;
    CHAR                szFileCreated[MAXALPHATIMEDATE+1];
    CHAR                szFileModified[MAXALPHATIMEDATE+1];
    CHAR               *szFileName;
    FILEOBJECT_MACEXT  *pMACFileObject;
    FILEOBJECT_HPFSEXT *pHPFSFileObject;

    /* This code assumes non-Unix environment such as Windows.
       On a Unix platform, for example, this code would need to be modified
       to convert the OBJECT_DESCRIPTOR structure from Domino canonical 
       format to host format.
    */

    pObject = (OBJECT_DESCRIPTOR*)pData;

    if ( pObject->ObjectType != OBJECT_FILE )
    {
        fprintf( dumpfile, "  Object Type = UNKNOWN (%#x).\n", 
                                                pObject->ObjectType );
        return;
    }
    fprintf( dumpfile, "  Object Type = OBJECT_FILE.\n" );

    pFileObject = (FILEOBJECT*)pData;

    /* get file name */
    wFileNameLen = pFileObject->FileNameLength;
    ((FILEOBJECT*)pData)++ ;
    pFileNameStart = (CHAR*)pData;
    szFileName = (CHAR*)malloc(wFileNameLen+1);
    memcpy( szFileName, pFileNameStart, wFileNameLen );
    szFileName[wFileNameLen] = '\0';
    fprintf( dumpfile, "  File Name = '%s'.\n", szFileName );
    free(szFileName);

```
**See Also :**
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
[NSFNoteDetachFile](/domino-c-api-docs/reference/Func/NSFNoteDetachFile)
[NSFNoteExtractFile](/domino-c-api-docs/reference/Func/NSFNoteExtractFile)
[OBJECT_DESCRIPTOR](/domino-c-api-docs/reference/Data/OBJECT_DESCRIPTOR)
[ODSReadMemory](/domino-c-api-docs/reference/Func/ODSReadMemory)
[_xxx (ODS Types)](/domino-c-api-docs/reference/Symb/_xxx (ODS Types))
---
