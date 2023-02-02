##### Function : Statistics Reporting
##### StatToText - Converts a statistic value to text.
---
##### #include <stats.h>
void LNPUBLIC **StatToText(**

	char far *Facility,
	char far *StatName,
	WORD  ValueType,
	void far *Value,
	char far *NameBuffer,
	WORD  NameBufferLen,
	char far *ValueBuffer,
	WORD  ValueBufferLen);
**Description :**
This function converts a statistic value to text.
**Parameters :**
Input :
Facility  -  Name of facility.  See Symbolic Value, STATPKG_xxx for a list of existing Domino facilities.

StatName  -  Name of statistic.

ValueType  -  Value type of the statistic:  See VT_xxx.

Value  -  Value of the statistic.

NameBufferLen  -  Length of the NameBuffer.

ValueBufferLen  -  Length of the ValueBuffer.

Output :
(routine)  -  None


NameBuffer  -  Pointer to a buffer that will receive a composite of the facility and statistic name as a NULL terminated string.

ValueBuffer  -  Pointer to a buffer that will receive the value of the statistic as a NULL terminated string.

**Sample Usage :**
```

   StatToText(Facility, StatName, ValueType, Value,
            NameBuffer, sizeof(NameBuffer)-1,
            ValueBuffer, sizeof(ValueBuffer)-1);

   sprintf(OutBuffer, "  %s = %s\n", NameBuffer, ValueBuffer);

```
**See Also :**
[STATPKG_xxx](D:/md_files/STATPKG_xxx.md)
[StatTraverse](D:/md_files/StatTraverse.md)
[VT_xxx](D:/md_files/VT_xxx.md)
---
