##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [NUMBER_RANGE] - Item Data Type - Number List/Range
---
```
#include <nsfdata.h>
```
**Description :**

Number List fields contain one or more numbers. They are stored in notes as 
items of TYPE_NUMBER_RANGE.  An item of TYPE_NUMBER_RANGE consists of a range 
header followed by an array of numbers, as follows:
RANGE         range header
NUMBER        number no. 0
NUMBER        number no. 1
...
NUMBER        number no. N


The range header is a RANGE data structure. The ListEntries member of the 
header is a USHORT that contains the number of NUMBERs in the list. Since 
ranges of numbers are not supported in Domino, the RangeEntries member of the 
header should be set to 0. 

After the header comes an array of NUMBERs. There are ListEntries NUMBERSs in 
the array.

In the Notes user interface, create a Number List field by composing a document 
using a form with a Number field that accepts multiple values. Enter one or 
more numbers, separated by multi-value separators, into the field. The Number 
field accepts multiple values if the design of the field in the form has the 
Allow Multi-Values box checked in the Field Definition dialog box. The 
multi-value separators are also defined by the design of the field in the form. 
The default multi-value separator for Number fields is a comma or a semicolon, 
but others may be used. 

To create a number list field from the API, allocate a block of memory 
sufficient to hold a RANGE data structure followed by as many NUMBERs as you 
need. Initialize a RANGE structure, then append it to the memory block. Append 
NUMBERs to the memory block following the RANGE. Finally, call NSFItemAppend 
specifying the memory block as the item value. Specify data type 
TYPE_NUMBER_RANGE. Domino and Notes automatically convert  items of type 
TYPE_NUMBER_RANGE to canonical format when appending them to a note, and 
convert them to host format when reading them from a note. Therefore, do not 
perform host/canonical conversion on this data.

The multi-value separator character is not stored in the number list field. 

The total length of a Number List field must not exceed 15 kilobytes. 

For Number List fields created using the Notes user interface, the SUMMARY flag 
is set by default. For Number List fields created using the API, specify 
ITEM_SUMMARY in the item_flags parameter of NSFItemAppend to set the SUMMARY 
flag.

**Sample Usage :**
```
#define LIST_COUNT 5

DBHANDLE    hDB;
NOTEHANDLE  hNote;
DWORD       dwValueLen;
void far   *pvoidItemValue;
RANGE      *pRange;
NUMBER     *pNumber;
WORD        i;
STATUS      error;
NUMBER      aNumbers[LIST_COUNT] = {1,3,9703.4,-7,0.11592};

dwValueLen = sizeof(RANGE) + (LIST_COUNT * sizeof(NUMBER));
pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);

pRange = (RANGE*)pvoidItemValue;
pRange->ListEntries = usCount;
pRange->RangeEntries = 0;
pRange++;
pNumber = (NUMBER*)pRange;

for (i = 0; i < LIST_COUNT; i++)
{
    *pNumber = aNumbers[i];
    pNumber++;
}

error = NSFItemAppend (hNote, 
            ITEM_SUMMARY,
            szFieldName, 
            strlen(szFieldName),
            TYPE_NUMBER_RANGE,
            pvoidItemValue, 
            dwValueLen);

free (pvoidItemValue);
```
**See Also :**
[NSFItemAppend](/reference/Func/NSFItemAppend)
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NUMBER](/reference/Data/NUMBER)
[RANGE](/reference/Data/RANGE)
[TYPE_xxx](/reference/Symb/TYPE_xxx)
---
