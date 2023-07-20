##### Symbolic Value : Import/Export
##### EXPKG_xxx - Offsets within PKG_EXPORT for exports.
---
```
#include <globerr.h>
```

**Symbolic Values :**

	EXPKG_XCGM	  -  Offset for CGM image export facility.

	EXPKG_XRTF	  -  Offset for RTF export facility.

	EXPKG_XSTF	  -  Offset for STF export facility.

	EXPKG_XSTR	  -  Offset for Structured Text export facility

	EXPKG_XTAB	  -  Offset for Tabular Text export facility.

	EXPKG_XTEXT	  -  Offset for Text export facility.

	EXPKG_XTIFF	  -  Offset for TIFF Image export facility.

	EXPKG_XW4W	  -  Offset for Word for Windows export facility.

	EXPKG_XWKS	  -  Offset for Lotus 1-2-3 export facility.

	EXPKG_ALL	  -  Offset for 20 common strings shared by all Notes import/export modules


**Description :**

On the Mac, since all ixports are compiled into Notes, their strings must have unique IDs, we avoid using a separate PKG for each by defining the offset of each ixport's first string.  Under Windows and PM, since each ixport is a separate DLL with separate DS space, all offsets are set to 0.<br>
<br>
NOTE:  TARGA, and WMF are not to be ported to the Mac, therefore no offsets are provided for them.


**See Also :**
[IMPKG_xxx](/domino-c-api-docs/reference/Symb/IMPKG_xxx)
---
