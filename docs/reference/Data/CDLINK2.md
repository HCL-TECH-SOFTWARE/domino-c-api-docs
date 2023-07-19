##### Data Type : Composite Data
##### CDLINK2 - Index into a DocLink Reference List
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 WSIG Header;
 WORD LinkID;   /* ID of the link */
       /* Now comes the variable part:             */
          /*   Null-terminated display comment        */
          /*   Null-terminated server "hint"          */
          /*   Null-terminated anchor text (optional) */
} CDLINK2;


**Description :**

This structure implements a document link in a rich text field.  It contains an index into a Doc Link Reference List.  A Doc Link Reference (a NOTELINK structure) contains all the information necessary to open the specified document from any database on any server. <br>
<br>
Notes creates two different types of Doc Links.  The first type consists of a CDLINK2 record and a Doc Link Reference.  The second type consists of a CDLINKEXPORT2 record.<br>
<br>
When a Notes user creates a Doc Link from the Notes editor, Notes creates the first type of Doc Link in the document.  This first type of Doc Link has two parts: a CDLINK2 record, and a DocLink Reference.  Warning: API programs that manipulate this type of Doc Link must keep the two parts synchronized. The CDLINK2 record resides in the rich text field. The DocLink Reference resides in the DocLink Reference List ($Links item). <br>
<br>
A CDLINK2 record consists of a header followed by an index. The index in the CDLINK2 identifies one of the NOTELINK  entries in the DocLink Reference List. The CDLINK2 record requires the Doc Link Reference List ($Links) item in order to resolve the link.  The CDLINK2 record is then followed by two or three consecutive null-terminated strings.  The first string contains the display comment for the link, identifying the source database, view, and document title.  The second string, called for obscure reasons the &quot;hint&quot;, contains the name of the Lotus Domino server where the link originated;  this string may be empty, in which case the null terminator must be present.  The third string, if present, contains the anchor text for the target CDANCHOR record for this link.  If the third string is present, the target document is searched for a CDANCHOR record with the matching text string.  If a CDANCHOR record with a matching string is found, Notes displays the target document beginning at the location of the CDANCHOR record.<br>
<br>
When a Notes user copies a section of rich text containing a Doc Link to the clipboard, then Notes converts the CDLINK2 record in the rich text to a CDLINKEXPORT2 before the data is exported to the clipboard.  Notes performs this conversion because the corresponding Doc Link Reference List ($Links) item is not also exported to the clipboard.  A CDLINKEXPORT2 record contains the NOTELINK information that a CDLINK2 structure does not have. Therefore, a CDLINKEXPORT2 will function properly in the context of other documents or databases where the original Doc Link Reference List ($Links) item is not available.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.


**Sample Usage :**
```
void  LNPUBLIC  DumpCDLink2 (char *RecordPtr, DWORD RecordLength)
{
    CDLINK2    *pCDLINK2;

    fprintf (dumpfile, "  LINK2\n");

    pCDLINK2 = (CDLINK2*)RecordPtr;
    fprintf (dumpfile, "\tLink ID = %d\n", pCDLINK2->LinkID);

    return;
}
```

**See Also :**
[CDANCHOR](/domino-c-api-docs/reference/Data/CDANCHOR)
[CDLINKEXPORT2](/domino-c-api-docs/reference/Data/CDLINKEXPORT2)
[LINK_VERSIONxxx](/domino-c-api-docs/reference/Symb/LINK_VERSIONxxx)
[NOTELINK](/domino-c-api-docs/reference/Data/NOTELINK)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
[TYPE_xxx [NOTELINK_LIST]](/domino-c-api-docs/reference/Symb/TYPE_xxx [NOTELINK_LIST])
---
