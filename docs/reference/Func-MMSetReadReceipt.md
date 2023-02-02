##### Function : MIME
##### MMSetReadReceipt - set Conversion Controls read receipt setting
---
##### #include <mailmisc.h>
void LNPUBLIC **MMSetReadReceipt(**

	CCHANDLE  hCC,
	WORD  wReadReceipt);
**Description :**
The function  MMSetReadReceipt sets the Conversions Controls read receipt 
setting to the input value, wReadReceipt.  No checking is done for out of 
bounds values.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wReadReceipt  -  the value to use for the Conversion Controls read receipt setting.

Output :
(routine)  -  void


**Sample Usage :**
```
MMSetReadReceipt(hCC, 0);     /* 0 - Do not pass read receipt requests when 
importing or exporting 
	   1 - Support read receipt requests (as Return-Receipt-To when 
exporting)
	   2 - Support read receipt requests (as Disposition-Notification-To 
when exporting) */

```
**See Also :**
[MMGetReadReceipt](D:/md_files/MMGetReadReceipt.md)
[CCHANDLE](D:/md_files/CCHANDLE.md)
---
