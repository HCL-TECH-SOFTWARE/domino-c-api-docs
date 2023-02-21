##### Function : Time
##### IntlTIMEDATESetValue - Set INTL_TIMEDATE_PROPERTY value.
---
```
#include <misc.h>
STATUS LNPUBLIC IntlTIMEDATESetValue(

	INTLTIMEDATEHANDLE  hTimeDateHandle,
	INTL_TIMEDATE_PROPERTY  prop,
	void *propValue);
```
**Description :**

Set the property value to either AMStringProperty or PMStringProperty defined 
in INTL_TIMEDATE_PROPERTY.

**Parameters :**
Input :
hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to IntlTIMEDATECreateHandle.

prop  -  either set the AMStringProperty or the PMStringProperty value.

propValue  -  value set for either the AMStringProperty or the PMStringProperty

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully set value

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```
char    UserDefinedString[]= "Intl Setting PM";
INTL_TIMEDATE_PROPERTY propValue;

propValue = PMStringProperty;
if(error = IntlTIMEDATESetValue(hTimeDate, propValue, UserDefinedString))
{
	IntlTIMEDATEDeleteHandle( hTimeDate );
	printf ("Error: unable to convert TIMEDATE to text.\n");
       TimeStringLen = 0;
	ItemText[TimeStringLen] = '\0';
	break;
}
```
**See Also :**
[IntlTIMEDATECreateHandle](/domino-c-api-docs/reference/Func/IntlTIMEDATECreateHandle)
[IntlTIMEDATEGetValue](/domino-c-api-docs/reference/Func/IntlTIMEDATEGetValue)
[INTL_TIMEDATE_PROPERTY](/domino-c-api-docs/reference/Data/INTL_TIMEDATE_PROPERTY)
[TIMEDATE](/domino-c-api-docs/reference/Data/TIMEDATE)
---
