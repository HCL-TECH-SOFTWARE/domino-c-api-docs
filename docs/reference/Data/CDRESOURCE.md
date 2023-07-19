##### Data Type : Composite Data
##### CDRESOURCE - A CD structure which defines a Domino Resource.
---
```
#include <rsrcods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD Flags;            /* one of CDRESOURCE_FLAGS_xxx */
   WORD  Type;             /* one of CDRESOURCE_TYPE_xxx */
   WORD  ResourceClass;    /* one of CDRESOURCE_CLASS_xxx */
   WORD  Length1;          /* meaning depends on Type */
   WORD  ServerHintLength; /* length of the server hint */
   WORD  FileHintLength;   /* length of the file hint */
   BYTE  Reserved[8];
/* Variable length follows:
 *   String of size ServerHintLength: hint as to resource's server
 *   String of size FileHintLength: hint as to resource's file
 * - if CDRESOURCE_TYPE_URL : 
 *     string of size Length1 - the URL.
 * - if CDRESOURCE_TYPE_NOTELINK: 
 *     if CDRESOURCE_FLAGS_NOTELINKINLINE is NOT set in Flags:
 *       WORD LinkID - index into $Links
 *       string of size Length1 - the anchor name (optional)
 *     if CDRESOURCE_FLAGS_NOTELINKINLINE is set in Flags:
 *       NOTELINK NoteLink
 *       string of size Length1 - the anchor name (optional)
 * - if CDRESOURCE_TYPE_NAMEDELEMENT :
 *  TIMEDATE ReplicaID (zero if current db)
 *  string of size Length1 - the name of element
 */
} CDRESOURCE;

**Description :**

This CD record defines a resource within a database.  There may be many resources defined within a particular database.  A resource can be an image, an applet, a shared field or a script library.
<ul><br>
<br>
WSIG	Header			Signature and length<br>
DWORD	Flags			CDRESOURCE_FLAGS_xxx<br>
WORD	Type			CDRESOURCE_TYPE_xxx<br>
WORD 	ResourceClass		CDRESOURCE_CLASS_xxx<br>
WORD	Length1			depends on type	<br>
WORD	ServerHintLength	length of the server hint<br>
WORD	FileHintLength		length of the file hint	<br>
BYTE	Reserved</ul>



**See Also :**
[CDRESOURCE_CLASS_xxx](/domino-c-api-docs/reference/Symb/CDRESOURCE_CLASS_xxx)
[CDRESOURCE_FLAGS_xxx](/domino-c-api-docs/reference/Symb/CDRESOURCE_FLAGS_xxx)
[CDRESOURCE_TYPE_xxx](/domino-c-api-docs/reference/Symb/CDRESOURCE_TYPE_xxx)
---
