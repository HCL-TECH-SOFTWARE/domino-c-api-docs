##### Function : Time
##### IntlTIMEDATECreateHandle - Create handle for International TIMEDATE functionality.
---
##### #include <misc.h>
STATUS LNPUBLIC **IntlTIMEDATECreateHandle(**

	INTLTIMEDATEHANDLE *hTimeDateHandle);
**Description :**
This function is called to initialize the INTLTIMEDATEHANDLE..  This function  
must be the first function called when setting up to convert a TIMEDATE to text 
using IntlTIMEDATEConvertToText.

**Parameters :**
Input :
hTimeDateHandle  -  an INTLTIMEDATEHANDLE handle

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully created handle.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


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
```
**See Also :**
[IntlTIMEDATEConvertToText](D:/md_files/IntlTIMEDATEConvertToText.md)
[IntlTIMEDATEDeleteHandle](D:/md_files/IntlTIMEDATEDeleteHandle.md)
[IntlTIMEDATEGetValue](D:/md_files/IntlTIMEDATEGetValue.md)
[INTLTIMEDATEHANDLE](D:/md_files/INTLTIMEDATEHANDLE.md)
[IntlTIMEDATESetValue](D:/md_files/IntlTIMEDATESetValue.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
