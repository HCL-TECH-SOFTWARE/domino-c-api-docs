##### Function : Time
##### TimeGMToLocal - Convert TIMEDATE to year, month, day, etc..
---
```
#include <misc.h>
BOOL LNPUBLIC TimeGMToLocal(

	TIME far *Time);
```
**Description :**

This function takes a TIME structure, converts the .GM member (binary TIMEDATE) 
into its constituent components, and assigns those values to the appropriate 
integer members of the same TIME structure. 

It is useful in bridging to data structures required by Operating Systems or 
'C' library time/date functions or in the process of converting a TIMEDATE 
value from one time zone to its equivalent value in an other time zone.

**Parameters :**
Input :
Time  -  A pointer to a TIME structure whose Time->GM member contains the TIMEDATE structure you wish to expand.

Output :
(routine)  -  Returns FALSE if successful and TRUE if not.


Time  -  The address of the TIME struture in which the constituent values of the Time->GM member are returned.


**Sample Usage :**
```
time_oid.GM = note_created_td;
if (TimeGMToLocal(&time_oid))
   goto Exit;
```
**See Also :**
[TimeLocalToGM](/domino-c-api-docs/reference/Func/TimeLocalToGM)
[TimeGMToLocalZone](/domino-c-api-docs/reference/Func/TimeGMToLocalZone)
[OSCurrentTimeZone](/domino-c-api-docs/reference/Func/OSCurrentTimeZone)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
---
