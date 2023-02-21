##### Data Type : Composite Data
##### CDEMBEDDEDEDITCTL - Specifies an embedded edit control.
---
```
#include <editods.h>
```
**Description :**

This CD record defines an embedded element of type 'editor'. It is preceded by 
a CDHOTSPOTBEGIN and a CDPLACEHOLDER. The CD record, CDPLACEHOLDER, further 
defines the CDEMBEDDEDEDITCTL. The fields in this record are:

	Header - Signature and Length of this CD record.
	Flags - Embedded edit control flags, see EMBEDDEDEDITCTL_FLAG_xxx.
	NameLength - Length of the optional embedded editor name. 
	SpareWord - Reserved for future use.
	SpareDWord -  Reserved for future use.

These fields are followed by the optional embedded editor name. If you plan to 
use it, you will need to declare the variable and assign a value to its length.


**See Also :**
[EMBEDDEDEDITCTL_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDEDITCTL_FLAG_xxx)
---
