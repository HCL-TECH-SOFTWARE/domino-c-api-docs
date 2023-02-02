##### Function : Time
##### TimeGMToLocalZone - Expand TIMEDATE using another time zone value.
---
##### #include <misc.h>
BOOL LNPUBLIC **TimeGMToLocalZone(**

	TIME far *Time);
**Description :**
This function takes the binary TIMEDATE structure and a specific time zone and 
DST setting, and converts it into its constituent components, and assigns those 
values to the appropriate (int) members of the TIME structure.   This can be 
used to convert a time to a given time zone.  The TimeGMToLocalZone and 
TimeLocalToGM pairing can be used to convert any TIMEDATE from one time zone to 
another.

Note:  If the TIMEDATE that is to be expanded contains only a date, and not a 
time, then you will need to set the time component ALLDAY in order to use this 
function.
**Parameters :**
Input :
Time  -  A pointer to a TIME structure whose time_ptr->GM member contains the TIMEDATE structure you wish to expand, and whose Time->zone and Time->dst are the desired time zone and DST setting.

Output :
(routine)  -  Returns FALSE if successful and TRUE if not.


Time  -  The address of the TIME structure in which the constituent (int) values of the Time->GM member are returned.

**Sample Usage :**
```
/* Convert from GMT to a local time zone the easy way */
time_seqnum.GM.Innards[0] = note_sequence_td.Innards[0];
time_seqnum.GM.Innards[1] = note_sequence_td.Innards[1];
if (TimeGMToLocalZone(&time_seqnum))
   goto Exit;

/* convert the (int) members back to the GM member */
if (TimeLocalToGM(&time_seqnum))
   goto Exit;
```
**See Also :**
[TimeGMToLocal](D:/md_files/TimeGMToLocal.md)
[TimeLocalToGM](D:/md_files/TimeLocalToGM.md)
[OSCurrentTimeZone](D:/md_files/OSCurrentTimeZone.md)
[OSCurrentTIMEDATE](D:/md_files/OSCurrentTIMEDATE.md)
---
