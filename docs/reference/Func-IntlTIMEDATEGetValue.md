##### Function : Time
##### IntlTIMEDATEGetValue - Get AMStringProperty or PMStringProperty value set.
---
##### #include <misc.h>
STATUS LNPUBLIC **IntlTIMEDATEGetValue(**

	INTLTIMEDATEHANDLE  hTimeDateHandle,
	INTL_TIMEDATE_PROPERTY  prop,
	WORD  valueLen,
	void *retpropValue);
**Description :**
Get the value set to either the AMStringProperty or PMStringProperty defined in 
INTL_TIMEDATE_PROPERTY.

**Parameters :**
Input :
hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to IntlTIMEDATECreateHandle.

prop  -  value set to get either the AMStringProperty or the PMStringProperty

valueLen  -  length of buffer to return value set for either AMStringProperty or PMStringProperty

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully get value

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retpropValue  -  returned property value of either the AMStringProperty or the PMStringProperty

**Sample Usage :**
```
char    UserDefinedString[]= "Intl Setting PM";
INTL_TIMEDATE_PROPERTY propValue;
char    retpropValue[YTSTRMAX];

propValue = PMStringProperty;
if(error = IntlTIMEDATESetValue(hTimeDate, propValue, UserDefinedString))
{
	IntlTIMEDATEDeleteHandle( hTimeDate );
	printf ("Error: unable to convert TIMEDATE to text.\n");
       TimeStringLen = 0;
	ItemText[TimeStringLen] = '\0';
	break;
}

if(error = IntlTIMEDATEGetValue(hTimeDate, propValue, sizeof(retpropValue), 
retpropValue))
{
	IntlTIMEDATEDeleteHandle( hTimeDate );
	printf ("Error: unable to convert TIMEDATE to text.\n");
       TimeStringLen = 0;
	ItemText[TimeStringLen] = '\0';
	break;
}
printf("\nPMStringProperty Value = %s:\n", retpropValue);
```
**See Also :**
[IntlTIMEDATECreateHandle](D:/md_files/IntlTIMEDATECreateHandle.md)
[INTLTIMEDATEHANDLE](D:/md_files/INTLTIMEDATEHANDLE.md)
[IntlTIMEDATESetValue](D:/md_files/IntlTIMEDATESetValue.md)
[INTL_TIMEDATE_PROPERTY](D:/md_files/INTL_TIMEDATE_PROPERTY.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
