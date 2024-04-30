##### Data Type : Views
##### VIEW_COLUMN_FORMAT6 - Extended View Column Format for additional View-Column properties in infobox.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct
	{
	WORD	Signature;					/* VIEW_COLUMN_FORMAT_SIGNATURE6 */
	WORD	dwLength;					/* sizeof this structure + any extra data. */
	/* formatting data. */
	DWORD	dwFlags6;						
	WORD	SequenceNumber;				/* Vertical Layout, Sequence Number for wrapping */
	WORD	IfViewIsNarrowDo;			/* Vertical Layout, if View is narrow */

	WORD	wAttributesLength;			/* length of random attributes list */
	WORD	wPubFieldLength;			/* length of fieldname to which this column is mapped for "publish on select" LI 3925.01 */
	WORD	LineNumber;					/* Line Number for Tile Viewer */
	WORD	TileViewer;					/* Action, if View is a Tile Viewer */
	DWORD	dwReserved[16];				/* Reserved for future use. */
	/* followed by PubField, then Attributes if present */
	} VIEW_COLUMN_FORMAT6;
```

**Description :**




**See Also :**
[VCF5_xxx](/domino-c-api-docs/reference/Symb/VCF5_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_COLUMN_FORMAT_SIGNATURE5](/domino-c-api-docs/reference/Symb/VIEW_COLUMN_FORMAT_SIGNATURE5)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
---
