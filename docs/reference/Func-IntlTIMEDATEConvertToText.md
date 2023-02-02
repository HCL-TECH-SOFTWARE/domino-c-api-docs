##### Function : Time
##### IntlTIMEDATEConvertToText - Convert an International TIMDEDATE to text.
---
##### #include <misc.h>
STATUS LNPUBLIC **IntlTIMEDATEConvertToText(**

	INTLTIMEDATEHANDLE  hTimeDateHandle,
	const void far *IntlFormat,
	const DTFMT *ExtTextFormat,
	WORD  DTFMTLen,
	const TIMEDATE *InputTime,
	WORD  TextBufferLength,
	char *retTextBuffer,
	WORD *retTextLength);
**Description :**
This function not only converts a Domino binary TIMEDATE structure into a 
character text string, it also allows the capability to add additional PM or AM 
String text to the converted TIMEDATE.

The DTFMT (Date Time Format) structure must be set and passed into 
IntlTIMEDATEConvertToText(..).  If the DTFMT structure is not set up then this 
function will default to the ConvertTIMEDATEToText(..) behavior.  The binary 
TIMEDATE will be converted to text, however there will be no additional 
processing on the text string of this TIMEDATE.

Note: Values that must be set within the DTFMT structure:

	DTFlags DT_VALID 
	  DT_SHOWTIME or DT_SHOWDATE
	  DT_STYLE_YMD or DT_STYLE_DMY or DT_STYLE_MDY

	DTDOWFmt refer to Day of Week Format values defined in DT_WFMT_xxx 

	DTYearFmt  refer to Year Format values defined in DT_YFMT_xxx

	DTMonthFmt refer to Month Format values defined in DT_MFMT_xxx

	DTDayFmt  refer to Day Format values defined in DT_DFMT_xxx

	If DTFlags is set to DT_SHOWTIME then DTTZone must be set to one of the 
values defined in TZFMT_xxx and DTTShow must be set to one of the  values 
defined in DT_TSHOW_xxx.

	If DTFlags is set to DT_SHOWDATE then DTDShow must be set to any of the 
values defined in DT_DSHOW_xxx.

DTDSpecial is optional and can be set to any one of the values defined in 
DT_DSPEC_xxx.



**Parameters :**
Input :
hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to IntlTIMEDATECreateHandle.


IntlFormat  -  The address of an INTLFORMAT structure in which the current international settings are returned.  Use OSGetIntlSettings(..) to get the INTLFORMAT structure. 

ExtTextFormat  -  The address of a DTFMT structure set up with the required fields.

DTFMTLen  -  Length of the DTFMT structure.

InputTime  -  A pointer to the Domino binary time/date structure that you want to convert.

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus one(1) , since it is recommended that the buffer be sized using MAXALPHATIMEDATE + 1, this is usually MAXALPHATIMEDATE.


Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully convert to text

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retTextBuffer  -  The address of a text buffer in which the character text Time/Date result of the conversion is returned.  It should be dimensioned to a length of MAXALPHATIMEDATE + 1 .  The text  returned is not NULL terminated.

retTextLength  -  The address of a WORD in which the length of the converted character text time/date text is returned.


**Sample Usage :**
```
char    UserDefinedString[]= "Intl Setting PM";
INTL_TIMEDATE_PROPERTY propValue;
INTLTIMEDATEHANDLE  hTimeDate;
INTLFORMAT   intlfmt;
char    retpropValue[YTSTRMAX];
DTFMT    dtFormat;

	OSGetIntlSettings(&intlfmt, sizeof(intlfmt));
	intlfmt.Flags |= TIME_AMPM_PREFIX;
	dtFormat.DTFlags = DT_VALID | DT_SHOWDATE | DT_SHOWTIME;
	dtFormat.DTDShow = DT_DSHOW_MDY;
	dtFormat.DTDSpecial = DT_DSPEC_21Y4;
	dtFormat.DTTZone = TZFMT_NEVER;
	if(intlfmt.Flags & DATE_YMD)
	 DT_SET_STYLE(dtFormat.DTFlags, DT_STYLE_YMD);
	else if(intlfmt.Flags & DATE_MDY)
	 DT_SET_STYLE(dtFormat.DTFlags, DT_STYLE_MDY);
	else if(intlfmt.Flags & DATE_DMY)
	 DT_SET_STYLE(dtFormat.DTFlags, DT_STYLE_DMY);

	if((intlfmt.Flags & DATE_4DIGIT_YEAR) || (intlfmt.Flags & 
DT_4DIGITYEAR))
	 dtFormat.DTYearFmt = DT_YFMT_YYYY;
	else
	 dtFormat.DTYearFmt = DT_YFMT_YY;

	if(dtFormat.DTFlags & DT_ALPHAMONTH)
	 dtFormat.DTMonthFmt = DT_MFMT_MMM;
	else
	 dtFormat.DTMonthFmt = DT_MFMT_MM;
	dtFormat.DTDayFmt = DT_DFMT_DD;
	dtFormat.DTDOWFmt = DT_WFMT_WWW;
	dtFormat.DTTShow = DT_TSHOW_ALL;

	if(intlfmt.Flags & CLOCK_24_HOUR)
	 dtFormat.DTFlags |= DT_24HOUR;
	else
	 dtFormat.DTFlags &= ~DT_24HOUR;


	dtFormat.DTDsep1 = intlfmt.DateString;
	dtFormat.DTDsep2 = intlfmt.DateString;
	dtFormat.DTDsep3 = intlfmt.DateString;
	dtFormat.DTTsep = intlfmt.TimeString;
...
...
...
	if(error = IntlTIMEDATECreateHandle( &hTimeDate ))
	{
        printf ("Error: unable to convert TIMEDATE to text.\n");
              TimeStringLen = 0;
	 ItemText[TimeStringLen] = '\0';
	 break;
       }
	propValue = PMStringProperty;
	if(error = IntlTIMEDATESetValue(hTimeDate, propValue, 
UserDefinedString))
	{
	 IntlTIMEDATEDeleteHandle( hTimeDate );
	 printf ("Error: unable to convert TIMEDATE to text.\n");
              TimeStringLen = 0;
	 ItemText[TimeStringLen] = '\0';
	 break;
       }
	if(error = IntlTIMEDATEGetValue(hTimeDate, propValue, 
sizeof(retpropValue), retpropValue))
	{
	 IntlTIMEDATEDeleteHandle( hTimeDate );
	 printf ("Error: unable to convert TIMEDATE to text.\n");
              TimeStringLen = 0;
	 ItemText[TimeStringLen] = '\0';
	 break;
	}
	printf("\nPMStringProperty Value = %s:\n", retpropValue);
	if(error = IntlTIMEDATEConvertToText(hTimeDate, &intlfmt, &dtFormat, 
sizeof(dtFormat), &TimeItem, MAXALPHATIMEDATE,
	      ItemText, &TimeStringLen))
	{
	 IntlTIMEDATEDeleteHandle( hTimeDate );
	 printf ("Error: unable to convert TIMEDATE to text.\n");
              TimeStringLen = 0;
	 ItemText[TimeStringLen] = '\0';
	 break;
	}
	IntlTIMEDATEDeleteHandle(hTimeDate);
       ItemText[TimeStringLen] = '\0';
       break;
```
**See Also :**
[DTFMT](D:/md_files/DTFMT.md)
[IntlTIMEDATECreateHandle](D:/md_files/IntlTIMEDATECreateHandle.md)
[IntlTIMEDATEDeleteHandle](D:/md_files/IntlTIMEDATEDeleteHandle.md)
[IntlTIMEDATEGetValue](D:/md_files/IntlTIMEDATEGetValue.md)
[INTLTIMEDATEHANDLE](D:/md_files/INTLTIMEDATEHANDLE.md)
[IntlTIMEDATESetValue](D:/md_files/IntlTIMEDATESetValue.md)
[INTL_TIMEDATE_PROPERTY](D:/md_files/INTL_TIMEDATE_PROPERTY.md)
[TIMEDATE](D:/md_files/TIMEDATE.md)
---
