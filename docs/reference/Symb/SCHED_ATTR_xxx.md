##### Symbolic Value : Calendaring and Scheduling
##### SCHED_ATTR_xxx - SCHED_ENTRY - Attr
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	SCHED_ATTR_FOREIGN_UNID	  -  Used by gateways to return foreign UNIDs

	SCHED_ATTR_REPEAT_EVENT	  -  In Release 5, identifies a repeating meeting.

	SCHED_ATTR_RESERVED4	  -  Bit 6 is reserved for future use.

	SCHED_ATTR_RESERVED8	  -  Bit 7 is reserved for future use.

	SCHED_ATTR_TYPE_BITS	  -  Entry type mask.

	SCHED_ATTR_FREE_BASE	  -  Entry types that don't block off busy time.

	SCHED_ATTR_BUSY_BASE	  -  Entry types that block off busy time.

	SCHED_ATTR_NULL	  -  (SCHED_ATTR_FREE_BASE + 0x00)

	SCHED_ATTR_PENCILED	  -  (SCHED_ATTR_FREE_BASE + 0x01)

	SCHED_ATTR_FREE_RESERVED2	  -  (SCHED_ATTR_FREE_BASE + 0x02)

	SCHED_ATTR_FREE_RESERVED3	  -  (SCHED_ATTR_FREE_BASE + 0x03)

	SCHED_ATTR_FREE_RESERVED4	  -  (SCHED_ATTR_FREE_BASE + 0x04)

	SCHED_ATTR_FREE_RESERVED5	  -  (SCHED_ATTR_FREE_BASE + 0x05)

	SCHED_ATTR_FREE_RESERVED6	  -  (SCHED_ATTR_FREE_BASE + 0x06)

	SCHED_ATTR_FREE_RESERVED7	  -  (SCHED_ATTR_FREE_BASE + 0x07)

	SCHED_ATTR_APPT	  -  (SCHED_ATTR_BUSY_BASE + 0x00)

	SCHED_ATTR_NONWORK	  -  (SCHED_ATTR_BUSY_BASE + 0x01)

	SCHED_ATTR_BUSY_RESERVED2	  -  (SCHED_ATTR_BUSY_BASE + 0x02)

	SCHED_ATTR_BUSY_RESERVED3	  -  (SCHED_ATTR_BUSY_BASE + 0x03)

	SCHED_ATTR_BUSY_RESERVED4	  -  (SCHED_ATTR_BUSY_BASE + 0x04)

	SCHED_ATTR_BUSY_RESERVED5	  -  (SCHED_ATTR_BUSY_BASE + 0x05)

	SCHED_ATTR_BUSY_RESERVED6	  -  (SCHED_ATTR_BUSY_BASE + 0x06)

	SCHED_ATTR_BUSY_RESERVED7	  -  (SCHED_ATTR_BUSY_BASE + 0x07)


**Description :**

Possible values for the Attr member of the SCHED_ENTRY structure.  Note that if bit 3 (bits are numbered from 0 to 7) is set, the entry will take up busy time.  The lower nibble of the attributes defines the the entry type.
<ul><br>
<br>
NOTE:  The upper two bits of the Attr field is reserved for future use (bit 6 - 7).</ul>



**See Also :**
[SCHED_ENTRY](/domino-c-api-docs/reference/Data/SCHED_ENTRY)
---
