##### Function : Time
##### ConvertTIMEDATEToText - Converts a binary TIMEDATE to a character text string.
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertTIMEDATEToText(

	const void far *IntlFormat,
	const TFMT far *TextFormat,
	const TIMEDATE far *InputTime,
	char far *retTextBuffer,
	WORD  TextBufferLength,
	WORD far *retTextLength);
```
**Description :**

This function converts a Domino binary TIMEDATE structure into a character text 
string. 

You may also optionally request a non-standard format for the output string by 
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard "current" 
settings is acceptable.

Note: If 4-digit year is specified in the date setting of the operating system, 
then the converted text will contain a 4-digit year.  If a 2-digit year is 
specified in the date setting of the operating system, and if the year portion 
of the date in the TIMEDATE structure is in the range 1950 to 1999, the 
converted text will only contain the last 2 digits of the year (e.g. "98".)  
Otherwise all 4 digits of the year will be represented (e.g. "2001".)   To 
represent all years, including 1950 to 1999, with 4 digits, specify TFMT.Date 
as either TDFMT_FULL4, TDFMT_CPARTIAL4, or  TDFMT_DPARTIAL4.

**Parameters :**
Input :
IntlFormat  -  The internationalization settings in effect. You retrieve these settings in an INTLFORMAT structure returned during a call to OSGetIntlSettings. This argument is a void pointer to the INTLFORMAT.   Can be NULL, in which case this function invokes OSGetIntlSettings and works with those settings for the duration of the call.

TextFormat  -  A pointer to a TFMT structure -- which specifies the desired format of the character text converted time/date string.    Can be NULL, in which case this function creates a temporary version of the required TFMT structure and assigns the following values to its members: 

td_format_ptr->Date = TDFMT_FULL;
td_format_ptr->Time = TTFMT_FULL;
td_format_ptr->Zone = TZFMT_NEVER;
td_format_ptr->Structure = TSFMT_DATETIME;


InputTime  -  A pointer to the Domino binary time/date structure that you want to convert.

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus one(1) , since it is recommended that the buffer be sized using MAXALPHATIMEDATE + 1, this is usually MAXALPHATIMEDATE.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - conversion successful. 
ERR_TDO_CONV - Invalid Time or Date Encountered.
ERR_IFMT - Invalid International Format Specifier.
ERR_TFMT - Invalid Time/Date Format Specifier.


retTextBuffer  -  The address of a text buffer in which the character text Time/Date result of the conversion is returned.  It should be dimensioned to a length of MAXALPHATIMEDATE + 1 .  The text  returned is not NULL terminated.

retTextLength  -  The address of a WORD in which the length of the converted character text time/date text is returned.


**Sample Usage :**
```
  
   /* Get Last modified time/date of note just created */

   NSFNoteGetInfo(note_handle, _NOTE_MODIFIED, &binary_td2);
   td_string_ptr = &td_string1[0];
   if (error_status = ConvertTIMEDATEToText(&intl_format, &td_format,
                                       &binary_td2, td_string_ptr,
                                       MAXALPHATIMEDATE, &string_len))
       goto Exit;
   td_string_ptr[string_len] = '\0';  /* provide NULL terminator */

```
**See Also :**
[ConvertTextToTIMEDATE](/reference/Func/ConvertTextToTIMEDATE)
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/reference/Func/OSGetIntlSettings)
[TFMT](/reference/Data/TFMT)
---
