##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [NOTEREF_LIST] - Item Data Type - Response Reference List
---
##### #include <nsfdata.h>
**Description :**
All response documents contain a Response Reference List item.  This item has 
field name "$REF" and data type TYPE_NOTEREF_LIST. The response reference list 
item identifies the main, or parent document. 

A response reference list item consists of a LIST header structure, followed 
by  the UNIVERSALNOTEID (UNID) of the parent document, as follows:
LIST
UNIVERSALNOTEID

To create a response document in a Domino database, first obtain the UNID of 
the parent document. Open or create the note that will be the response note. 
Then initialize a buffer that consists of a LIST structure followed by the UNID 
of the parent. Call NSFItemAppend to append this buffer to the note. Use the 
symbolic constant FIELD_LINK (defined as "$REF") to specify the field name. 
Specify data type TYPE_NOTEREF_LIST.

Domino and Notes automatically convert items of type TYPE_NOTEREF_LIST to 
canonical format when appending them to a note, and convert them to host format 
when reading them from a note. Therefore, do not perform host/canonical 
conversion on this data.
**Sample Usage :**
```
STATUS LNPUBLIC AppendRefItem( NOTEHANDLE hRespNote, OID oidMainNote)
{
    STATUS      error = NOERROR;
   DWORD       dwValueLen;
   char       *buf;
   LIST       ListHdr;
   UNID       NoteUNID;

    dwValueLen = sizeof(LIST) + sizeof(UNID);

    buf =  (char *)malloc(sizeof(LIST) + sizeof(UNID));
    if (buf == NULL)
    {
         printf ("Error: unable to allocate %lu bytes memory.\n", dwValueLen);
         return(ERR_AUTH_FLD_MALLOC);
    }

    /* Initialize the LIST header part of the response reference list */
    ListHdr.ListEntries = (USHORT) 1;

    /* Initialize the UNID part of the response reference list */
    NoteUNID.File = oidMainNote.File; /* user-unique identifier */
    NoteUNID.Note = oidMainNote.Note; /* time/date when the note was created */

    /* Pack the LIST and the UNID members of the Noteref list into
       a memory block.
    */
    memcpy(buf, (char*)&ListHdr, sizeof(LIST));
    memcpy((buf + sizeof(LIST)), (char*)&NoteUNID, sizeof(UNID));

    if (error = NSFItemAppend ( hRespNote,
                                ITEM_SUMMARY,
                                FIELD_LINK,             /* "$REF" */
                                strlen(FIELD_LINK),
                                TYPE_NOTEREF_LIST,      /* $REF data type */
                                buf,
                                dwValueLen))
    {
        printf ("Error: unable to append Note Reference List to Response.\n")
    }
    free (buf);
    return (error);
}

```
**See Also :**
[LIST](D:/md_files/LIST.md)
[UNIVERSALNOTEID](D:/md_files/UNIVERSALNOTEID.md)
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
---
