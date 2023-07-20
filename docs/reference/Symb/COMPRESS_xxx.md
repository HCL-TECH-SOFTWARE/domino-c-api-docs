##### Symbolic Value : Note
##### COMPRESS_xxx - Types of compression used for file attachments.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	COMPRESS_NONE	  -  Indicates that no compression algorithm is used.

	COMPRESS_HUFF	  -  Indicates that the attached file is encoded using a Huffman algorithm.

	COMPRESS_MASK	  -  Used for NSFNoteAttachFile() - Encoding argument.

	COMPRESS_LZ1	  -  Indicates that the attached file is encoded using LZ1 compression.

	RECOMPRESS_HUFF	  -  Indicates that the attached file is re-compressed with Huffman compression, even if LZ1 is supported.


**Description :**

Specifies compression algorithm used when attaching file to a note.


**See Also :**
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
---
