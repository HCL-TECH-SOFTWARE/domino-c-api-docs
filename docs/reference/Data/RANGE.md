##### Data Type : Item (Field) Information
##### RANGE - Used to specify multiple values in a data field.
---
```
#include <global.h>
```
**Description :**

This structure is used to specify a data field that contains more than one 
value.  There are two ways to specify multiple values in a data field:  a list 
of values or a range of values.  A list is made up of one or more items of a 
datatype, separated by a delimiter.  A range is made up of consecutive data 
given the start and end of the data.  Note that not all datatypes support both 
lists and ranges.

The value in the ListEntries field of RANGE is the number of items specified in 
a delimited list of items.

The value in the RangeEntries field of RANGE is the number of item pairs 
specified as ranges.


**Sample Usage :**
```

NOTEHANDLE     hNote;
char          *szFieldName;
TIMEDATE      *aTimeDates;
WORD           usCount;
DWORD          dwValueLen;
void far      *pvoidItemValue;
RANGE         *pRange;
TIMEDATE      *pTimeDate;
WORD           i;
STATUS         error;

dwValueLen = sizeof(RANGE) + (usCount * sizeof(TIMEDATE));
pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);

pRange = (RANGE*)pvoidItemValue;
pRange->ListEntries = usCount;
pRange->RangeEntries = 0;
pRange++;
pTimeDate = (TIMEDATE*)pRange;

for (i = 0; i < usCount; i++)
{
    *pTimeDate = aTimeDates[i];
    pTimeDate++;
}
    
error = NSFItemAppend (hNote, ITEM_SUMMARY,
                szFieldName, strlen(szFieldName),
                TYPE_TIME_RANGE,
                pvoidItemValue, dwValueLen);

free (pvoidItemValue);
```
**See Also :**
[TYPE_xxx [NUMBER_RANGE]](/reference/Symb/TYPE_xxx [NUMBER_RANGE])
[TYPE_xxx [TIME_RANGE]](/reference/Symb/TYPE_xxx [TIME_RANGE])
---
