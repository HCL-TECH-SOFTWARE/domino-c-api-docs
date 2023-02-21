##### Function : Time
##### ConvertTextToTIMEDATE - Converts a character time/date string to TIMEDATE.
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertTextToTIMEDATE(

	const void far *IntlFormat,
	const TFMT far *TextFormat,
	char far * far *Text,
	WORD  MaxLength,
	TIMEDATE far *retTIMEDATE);
```
**Description :**

This function converts a character time/date string into Domino binary TIMEDATE 
format. 

You may also optionally request a non-standard format for the time/date string 
by setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard 
"current" settings are  acceptable.

The year portion of the time/date string may be specified with all 4 digits.  
If the date format does not require a 4-digit year, then the years 1950 to 2049 
may also be specified using only the last 2 digits.

Only integral values in the text string are converted.  If the seconds 
component of the string contains a decimal point, it will be truncated to its 
integer value.

**Parameters :**
Input :
IntlFormat  -  A pointer to a structure containing the internationalization settings in effect. You retrieve these settings in an INTLFORMAT structure by calling OSGetIntlSettings.  This must be done BEFORE calling ConvertTextToTIMEDATE.  Can be NULL, in which case this function invokes OSGetIntlSettings and works with those settings for the duration of the call.

TextFormat  -  A pointer to a TFMT structure -- which specifies the syntax of the date/time text string.   This structure must be populated by you before calling ConvertTextToTIMEDATE. See TDFMT_xxx, TTFMT_xxx, TZFMT_xxx, and TSFMT_xxx for an explanation of the definitions.   Can be NULL, in which case this function creates the required TFMT structure and assigns the following values to its members: 

td_format_ptr->Date = TDFMT_FULL;
td_format_ptr->Time = TTFMT_FULL;
td_format_ptr->Zone = TZFMT_NEVER;
td_format_ptr->Structure = TSFMT_DATETIME;


Text  -  A pointer to a pointer to the buffer containing the character time/date text. This buffer should have a maximum length of MAXALPHATIMEDATE + 1.

MaxLength  -  The maximum number of significant characters in Text, usually MAXALPHATIMEDATE.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - Conversion successful. 
ERR_TDI_CONV - Unable to interpret Time or Date.  This error indicates that the character time/date string is not in the correct format.  A common cause for this error is an incorrect date format.  The validity of a date format depends on the date separator that is chosen in the operating environment control panel.  The default separator in the Windows operating environment is a slash (/).  Refer to the Lotus Domino Designer documentation for more information about time/date formats.
ERR_IFMT - Invalid International Format Specifier.
ERR_TFMT - Invalid time/date Format Specifier.


Text  -  The specified pointer is updated to the next character after the time/date text that was parsed.

retTIMEDATE  -  The address of a TIMEDATE structure in which the binary equivalent of the time/date text is returned.


**Sample Usage :**
```
   /* Build a time/date string & convert to binary TIMEDATE structure*/

   strcpy(td_string1, "07");
   strcpy(&td_string1[strlen(td_string1)], intl_format.DateString);
   strcpy(&td_string1[strlen(td_string1)], "04");
   strcpy(&td_string1[strlen(td_string1)], intl_format.DateString);
   strcpy(&td_string1[strlen(td_string1)], "91 4");
   strcpy(&td_string1[strlen(td_string1)], intl_format.TimeString);
   strcpy(&td_string1[strlen(td_string1)], "30 PM EST");
   td_string_ptr = &td_string1[0];

   if (error_status = ConvertTextToTIMEDATE(&intl_format, &td_format,
                                    &td_string_ptr, strlen(td_string1),
                                    &binary_td1))
       goto Exit;
```
**See Also :**
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/domino-c-api-docs/reference/Func/OSGetIntlSettings)
[TFMT](/domino-c-api-docs/reference/Data/TFMT)
[TYPE_xxx [TIME_RANGE]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TIME_RANGE])
---
