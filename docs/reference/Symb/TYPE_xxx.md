##### Symbolic Value : Field
##### TYPE_xxx - Item Data Type definitions.
---
```
#include <nsfdata.h>
```
**Description :**

These values define the datatype of an item (field) in a note.

All datatypes below are passed to NSF in either host (machine-specific byte 
ordering and padding) or canonical form (Intel 86 packed form).  The format of 
each datatype, as it is passed to and from NSF functions, is listed below in 
the comment field next to each of the data types.  (This host/canonical issue 
is NOT applicable to Intel86 machines, because on that machine, they are the 
same and no conversion is required).  On all other machines, use the ODS 
subroutine package to perform conversions of those datatypes in canonical 
format before they can be interpreted.

Here is the format of the various LIST data types:

TYPE_TEXT_LIST:
    LIST /* list header */
    USHORT ... /* array of text string lengths following */
    text /* now comes the packed text for all strings */

TYPE_NUMBER_RANGE:
    RANGE /* range header */
    NUMBER ... /* array of NUMBERs */
    NUMBER_PAIR ... /* array of NUMBER_PAIRs */

TYPE_TIME_RANGE:
    RANGE /* range header */
    TIMEDATE ... /* array of time/date's */
    TIMEDATE_PAIR ... /* array of time/date pairs */

TYPE_NOTEREF_LIST:
    LIST /* list header */
    UNIVERSALNOTEID /* array of UNIVERSALNOTEIDs */

TYPE_NOTELINK_LIST:
    LIST /* list header */
    NOTELINK ... /* array of NOTELINKs */
 
TYPE_USERDATA:
    BYTE Length /* length of LMBCS "format-name" string */
    char[Length]; /* LMBCS "format-name" string used to distinguish various 
formats of user
                                  data that follows. ("format-name" string is 
NOT NULL-TERMINATED!) */
    data /* next is variable-length data that corresponds to the format 
specified by the string */

**See Also :**
[NSFItemAppend](/reference/Func/NSFItemAppend)
---
