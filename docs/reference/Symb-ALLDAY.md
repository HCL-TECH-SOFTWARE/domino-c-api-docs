##### Symbolic Value : Time
##### ALLDAY - Wildcard value for the Time portion of a TIMEDATE data structure.
---
##### #include <misc.h>
**Description :**
Wildcard value for the Time portion of a TIMEDATE data structure. Functions 
that test or compare a TIMEDATE in which the Time portion is set to ALLDAY will 
succeed for the Time portion of a TIMEDATE. For example: 
Suppose you have two TIMEDATES (td1 and td2) that are identical, except 
td1.Time = ALLDAY and td2.Time = 2000.  If you compare them as follows:
  td_compare_result = TimeDateCompare(&td1, &td2);
 The integer returned in td_compare_result will be 0, indicating that the two 
TIMEDATEs are equal.
**See Also :**
[ANYDAY](D:/md_files/ANYDAY.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
