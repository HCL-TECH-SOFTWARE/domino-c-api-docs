##### Symbolic Value : Note
##### HOST_xxx - File attachment definitions.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	HOST_MSDOS	  -  Attached file is in DOS format. Each line in the file ends with <carriage return><newline>, with an optional ^Z at the end of the file.

	HOST_OLE	  -  The internal format of the file is unknown to Domino. The format is defined by the application that attached the file.

	HOST_MAC	  -  Attached file is in Macintosh format.

	HOST_UNKNOWN	  -  The attached file came in through a gateway, and its internal format is unknown.

	HOST_HPFS	  -  The attached file is in High Performance File System format. It may contain exended attributes and long filenames.

	HOST_OLELIB	  -  Attached file is an encapsulated OLE object.

	HOST_BYTEARRAY_EXT	  -  OLE 2 ILockBytes byte array extent table. Used to be HOST_DOCFILE (Attached file is an OLE 2.0 compound file).

	HOST_BYTEARRAY_PAGE	  -  OLE 2 ILockBytes byte array page.

	HOST_MASK	  -  Used for NSFNoteAttachFile() - Encoding argument.

	HOST_CDSTORAGE	  -  Externally stored CD records. Multiple blocks of CD records may be stored. The storage contains a WORD with the number of blocks, a WORD for each block with the length of the block, a WORD containing TYPE_COMPOSITE, and the actual CD records.

	HOST_STREAM	  -  Binary private stream.

	HOST_LINK	  -  Contains a RESOURCELINK to a named element.

	HOST_LOCAL	  -  Used only as an argument to NSFNoteAttachFile, this specifies that the file should be attached using the host type of the local operating system.


**Description :**

Specifies the file type used when attaching file to a note.


**See Also :**
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
---
