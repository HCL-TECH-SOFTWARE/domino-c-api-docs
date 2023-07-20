##### Symbolic Value : Views
##### VIEW_CLASS_xxx - Upper four bits of the BYTE ViewStyle member of the VIEW_FORMAT_HEADER structure.
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VIEW_CLASS_TABLE	  -  Table class view.

	VIEW_CLASS_CALENDAR	  -  Calendar class view.

	VIEW_CLASS_MASK	  -  Bit mask for the VIEW_CLASS_xxx values.


**Description :**

These symbols specify the which of the upper four bits are set in the BYTE ViewStyle member of the VIEW_FORMAT_HEADER structure.  These four bits specify the class of a view (ie:  calendar or table view).  The lower four bits of the ViewStyle member further define the style of a view style.


**See Also :**
[VIEW_FORMAT_HEADER](/domino-c-api-docs/reference/Data/VIEW_FORMAT_HEADER)
---
