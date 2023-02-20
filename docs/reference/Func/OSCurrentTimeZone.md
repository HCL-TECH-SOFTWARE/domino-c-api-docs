##### Function : Time
##### OSCurrentTimeZone - Get current time zone and daylight saving state.
---
```
#include <ostime.h>
void LNPUBLIC OSCurrentTimeZone(

	int far *retZone,
	int far *retDST);
```
**Description :**

This function gets the current time zone and daylight savings time state.  It 
is a more convenient method than OSGetIntlSettings, but both functions return 
the same values for time zone and daylight savings time state.  A NULL may be 
used for either argument if only one value is desired.

**Parameters :**

Output :
(routine)  -  None.


retZone  -  The address of an integer (int) in which the time zone offset from Greenwich Mean Time is returned.  If NULL is specified, this value is not returned.  The value will be either an integer in the range -12 to +12, or 4 decimal digits.  The 4-digit format is used for time zones that have a fraction of an hour in the difference.  In this case, the high-order digits represent the number of minutes (either 30 or 45).  For example, the timezone for Iran is GMT - 3 1/2 hours;  this will be stored as -3003 (30 minutes and 03 hours).  The time zone acronyms associated with the offsets are:

-12         ZE12      Twelve Hours East of GMT
-4512    ZE12C   12 3/4 Hours East of GMT
-11         ZE11      Eleven Hours East of GMT
-3011    ZE10B   10 1/2 Hours East of GMT
-10         EAT       Eastern Autstralia Time
-9           CAT       Central  Autstralia Time
-3009    ZE9B     9 1/2 Hours East of GMT
-8           WAT      Western Autstralia Time
-7           ZE7        Seven Hours East of GMT
-6           ZE6        Six Hours East of GMT
-3006    ZE6B     6 1/2 Hours East of GMT
-5           ZE5        Five Hours East of GMT
-4505    ZE5C     5 3/4 Hours East of GMT
-3005    ZE5B     5 1/2 Hours East of GMT
-4           ZE4        Four Hours East of GMT
-3004    ZE4B     4 1/2 Hours East of GMT
-3           ZE3        Three Hours East of GMT
-3003    ZE3B     3 1/2 Hours East of GMT
-2           ZE2        Two Hours East of GMT
-1           CET       Central European Time
 0           GMT       Greenwich Mean Time
+1          ZW1       One Hour West of GMT
+2          ZW2       Two Hours West of GMT
+3          ZW3       Three Hours West of GMT
+3003   NST        Newfoundland
+4          AST        Atlantic Standard Time
+5          EST        Eastern Standard Time
+6          CST        Central Standard Time
+7          MST       Mountain Standard Time
+8          PST        Pacific Standard Time
+9          YST        Yukon Standard Time
+3009   ZW9B    9 1/2 Hours West of GMT
+10        HST       Hawaiin Standard Time
+11        BST       Bering Standard Time
+12        ZW12    Twelve Hours West of GMT

retDST  -  The address of an integer (int) in which the daylight savings time (DST) value for the current time zone is returned. 1 = YES and 0 = NO or it's not observed in this time zone.  Example: 0 for Eastern Standard Time (EST) or 1 for Eastern Daylight Time (EDT).  If NULL is specified, this value is not returned. 


**Sample Usage :**
```

   OSCurrentTimeZone(&zone_num, &ifdst);

```
**See Also :**
[TimeLocalToGM](/reference/Func/TimeLocalToGM)
[TimeGMToLocal](/reference/Func/TimeGMToLocal)
[TimeGMToLocalZone](/reference/Func/TimeGMToLocalZone)
---
