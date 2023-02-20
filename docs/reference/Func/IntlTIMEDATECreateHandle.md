##### Function : Time
##### IntlTIMEDATECreateHandle - Create handle for International TIMEDATE functionality.
---
```
#include <misc.h>
STATUS LNPUBLIC IntlTIMEDATECreateHandle(

	INTLTIMEDATEHANDLE *hTimeDateHandle);
```
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
[IntlTIMEDATEConvertToText](/reference/Func/IntlTIMEDATEConvertToText)
[IntlTIMEDATEDeleteHandle](/reference/Func/IntlTIMEDATEDeleteHandle)
[IntlTIMEDATEGetValue](/reference/Func/IntlTIMEDATEGetValue)
[INTLTIMEDATEHANDLE](/reference/Data/INTLTIMEDATEHANDLE)
[IntlTIMEDATESetValue](/reference/Func/IntlTIMEDATESetValue)
[TIMEDATE](/reference/Data/TIMEDATE)
---
