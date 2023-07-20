##### Symbolic Value : DDE
##### DDEFORMAT_xxx - DDE clipboard format.
---
```
#include <editods.h>
```

**Symbolic Values :**

	DDEFORMAT_TEXT	  -  CF_TEXT

	DDEFORMAT_METAFILE	  -  CF_METAFILE or CF_METAFILEPICT

	DDEFORMAT_BITMAP	  -  CF_BITMAP

	DDEFORMAT_RTF	  -  Rich Text Format

	DDEFORMAT_OWNERLINK	  -  OLE Ownerlink (never saved in CD_DDE or CD_OLE: used at run time).

	DDEFORMAT_OBJECTLINK	  -  OLE Objectlink (never saved in CD_DDE or CD_OLE: used at run time).

	DDEFORMAT_NATIVE	  -  OLE Native (never saved in CD_DDE or CD_OLE: used at run time).

	DDEFORMAT_ICON	  -  Program Icon for embedded object

	DDEFORMAT_TYPES	  -  Total number of DDE format types supported (Only relevant to persistent, on-disk stored types).


**Description :**

These values specify the DDE clipboard format with which data should be rendered.  They are used in the CDDDEBEGIN structure and in the CDOLEBEGIN structure.


**See Also :**
[CDDDEBEGIN](/domino-c-api-docs/reference/Data/CDDDEBEGIN)
[CDOLEBEGIN](/domino-c-api-docs/reference/Data/CDOLEBEGIN)
---
