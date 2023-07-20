##### Symbolic Value : Import/Export
##### IMPKG_xxx - Offsets within PKG_IMPORT for imports.
---
```
#include <globerr.h>
```

**Symbolic Values :**

	IMPKG_IFL	  -  Offset for CGM image import facility.

	IMPKG_IPCX	  -  Offset for PCX image import facility.

	IMPKG_IPIC	  -  Offset for Lotus PIC import facility.

	IMPKG_IRTF	  -  Offset for RTF import facility.

	IMPKG_ISTF	  -  Offset for STF import facility.

	IMPKG_ISTR	  -  Offset for Structured Text import facility

	IMPKG_ITAB	  -  Offset for Tabular Text export facility.

	IMPKG_ITARGA	  -  Offset for TARGA import facility.

	IMPKG_ITEXT	  -  Offset for Text import facility.

	IMPKG_ITIFF	  -  Offset for TIFF Image import facility.

	IMPKG_IW4W	  -  Offset for Word for Windows import facility.

	IMPKG_IWKSE	  -  Offset for Lotus 1-2-3 import facility, view level import.

	IMPKG_IWKSV	  -  Offset for Lotus 1-2-3 import facility, edit level import.

	IMPKG_IWMF	  -  Offset for WMF import facility.

	IMPKG_IBMP	  -  Offset for BMP import facility.

	IMPKG_IGIF	  -  Offset for GIF image import facility.

	IMPKG_ISTRNGS	  -  Offset for Binary with Text import facility.

	IMPKG_IJPEG	  -  Offset for JPEG image import facility.

	IMPKG_ALL	  -  Offset for 20 common strings shared by all Notes import/export modules


**Description :**

On the Mac, since all ixports are compiled into Notes, their strings must have unique IDs, we avoid using a separate PKG for each by defining the offset of each ixport's first string.  Under Windows and PM, since each ixport is a separate DLL with separate DS space, all offsets are set to 0.<br>
<br>
NOTE:  W4W and WMF are not to be ported to the Mac, therefore no offsets are provided for them.


**See Also :**
[EXPKG_xxx](/domino-c-api-docs/reference/Symb/EXPKG_xxx)
---
