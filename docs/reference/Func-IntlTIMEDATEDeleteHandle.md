##### Function : Time
##### IntlTIMEDATEDeleteHandle - Delete handle to International TIMEDATE functionality.
---
##### #include <misc.h>
void LNPUBLIC **IntlTIMEDATEDeleteHandle(**

	INTLTIMEDATEHANDLE  hTimeDateHandle);
**Description :**
Delete the INTLTIMEDATEHANDLE allocated with IntlTIMEDATECreateHandle.
**Parameters :**
Input :
hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to IntlTIMEDATECreateHandle(..).

Output :
(routine)  -  None


**Sample Usage :**
```
INTLTIMEDATEHANDLE hTimeDate;

if(error = IntlTIMEDATECreateHandle( &hTimeDate ))
{
	printf ("Error: unable to convert TIMEDATE to text.\n");
       TimeStringLen = 0;
	ItemText[TimeStringLen] = '\0';
	break;
}
...
...
...
IntlTIMEDATEDeleteHandle(hTimeDate);
```
**See Also :**
[IntlTIMEDATECreateHandle](D:/md_files/IntlTIMEDATECreateHandle.md)
[INTLTIMEDATEHANDLE](D:/md_files/INTLTIMEDATEHANDLE.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
