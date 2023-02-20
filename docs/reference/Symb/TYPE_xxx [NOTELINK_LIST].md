##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [NOTELINK_LIST] - Item Data Type - DocLink Reference List
---
```
#include <nsfdata.h>
```
**Description :**

Domino and Notes append a DocLink Reference List item to documents that contain 
Doc Links.  A DocLink Reference Item has field name "$Links".  The internal 
(API level) data type is TYPE_NOTELINK_LIST. Domino and Notes use the DocLink 
Reference List to resolve Doc Links in the rich text field.

A DocLink Reference List item consists of a LIST header structure, followed by 
an array of NOTELINK structures, as follows:
LIST
NOTELINK
NOTELINK
...


The LIST header identifies how many NOTELINK structures follow. The list 
contains one entry for every CDLINK2 record in the document.
Doc Links created from the Notes user interface have two parts: a CDLINK2 
record, and a DocLink Reference.  The CDLINK2 record resides in the rich text 
field. The DocLink Reference resides in the DocLink Reference List. 

A CDLINK2 record consists of a header followed by an index. The index in the 
CDLINK2 identifies one of the NOTELINK  entries in the DocLink Reference List.

The header of a CDLINK2 is a WSIG and the index is a WORD.

A NOTELINK contains all the information necessary to open a specific document 
from any database or server. When a user launches a Doc Link by double-clicking 
on the icon in the rich text field, Domino and Notes use the index in the 
CDLINK2 structure to get the corresponding NOTELINK from the DocLink Reference 
List. 

There are two types of DocLinks. The first type consists of a CDLINK2 record 
and a DocLink Reference.  The second type consists of a CDLINKEXPORT2 record. 

When a user initially creates a Doc Link in a document, the result is the first 
type of Doc Link.  However, when a user copies a DocLink from a rich text field 
to the clipboard, Domino and Notes convert the CDLINK2 structure to a 
CDLINKEXPORT2 structure in the data that is copied to the clipboard. If this 
clipboard data is pasted into the rich text field of another Domino document, 
the resulting Doc Link is the second type of Doc Link.

**Sample Usage :**
```
/************************************************************************

    FUNCTION:   DumpNotelinkList

    A NOTELINK List is a LIST followed by an array of NOTELINK structures.

    A NOTELINK structure universally (across all servers) describes
    a note LINK:
                typedef struct 
                {
                    TIMEDATE File;
                 UNID View;
                 UNID Note;
                } NOTELINK;

*************************************************************************/

void  LNPUBLIC  DumpNotelinkList (PCHAR pData, WORD length)
{
    LIST        List;
    USHORT      ListEntries, i;
    NOTELINK   *pNoteLink;
    TIMEDATE    tdFile ;   
    UNID        unidView;
  UNID        unidNote;

    List = *((LIST*)pData);
    ListEntries = List.ListEntries;
    ((LIST*)pData)++;
    fprintf (dumpfile, "\tlist has %d NOTELINKs\n", ListEntries);

    for (i = 0; i<ListEntries; i++,((NOTELINK *)pData)++)
    {
        fprintf (dumpfile, "\tNotelink #%d:\n", i+1);
        pNoteLink = (NOTELINK *)pData;
        tdFile = pNoteLink->File;
        unidView = pNoteLink->View;
        unidNote = pNoteLink->Note;
        fprintf (dumpfile, "\t Database replica ID = %#.4lx - %#.4lx\n", 
                    tdFile.Innards[1],
                    tdFile.Innards[0]);
        fprintf (dumpfile, "\t View UNID.File = %#.4lx - %#.4lx\n",
                    unidView.File.Innards[1],
                    unidView.File.Innards[0]);
        fprintf (dumpfile, "\t View UNID.Note = %#.4lx - %#.4lx\n",
                    unidView.Note.Innards[1],
                    unidView.Note.Innards[0]);
        fprintf (dumpfile, "\t Note UNID.File = %#.4lx - %#.4lx\n",
                    unidNote.File.Innards[1],
                    unidNote.File.Innards[0]);
        fprintf (dumpfile, "\t Note UNID.Note = %#.4lx - %#.4lx\n",
                    unidNote.Note.Innards[1],
                    unidNote.Note.Innards[0]);
    }

    return;
}
```
**See Also :**
[CDLINK2](/reference/Data/CDLINK2)
[CDLINKEXPORT2](/reference/Data/CDLINKEXPORT2)
[LIST](/reference/Data/LIST)
[NOTELINK](/reference/Data/NOTELINK)
[TYPE_xxx](/reference/Symb/TYPE_xxx)
[TYPE_xxx [NOTEREF_LIST]](/reference/Symb/TYPE_xxx [NOTEREF_LIST])
---
