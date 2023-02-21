##### Function : Time
##### IntlTIMEDATEDeleteHandle - Delete handle to International TIMEDATE functionality.
---
```
#include <misc.h>
void LNPUBLIC IntlTIMEDATEDeleteHandle(

	INTLTIMEDATEHANDLE  hTimeDateHandle);
```
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
[IntlTIMEDATECreateHandle](/domino-c-api-docs/reference/Func/IntlTIMEDATECreateHandle)
[INTLTIMEDATEHANDLE](/domino-c-api-docs/reference/Data/INTLTIMEDATEHANDLE)
[TIMEDATE](/domino-c-api-docs/reference/Data/TIMEDATE)
---
