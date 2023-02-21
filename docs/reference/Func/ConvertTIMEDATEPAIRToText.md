##### Function : Time
##### ConvertTIMEDATEPAIRToText - Converts binary TIMEDATE_PAIR to a character text string.
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertTIMEDATEPAIRToText(

	const void far *IntlFormat,
	const TFMT far *TextFormat,
	const TIMEDATE_PAIR far *InputTime,
	char far *retTextBuffer,
	WORD  TextBufferLength,
	WORD far *retTextLength);
```
**Description :**

This function converts a Domino binary TIMEDATE_PAIR structure into a character 
text string.   The character text string consists of two date strings separated 
by " - ".

You may also optionally request a non-standard format for the output string by 
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard "current" 
settings is acceptable.

**Parameters :**
Input :
IntlFormat  -  The internationalization settings in effect. You retrieve these settings in an INTLFORMAT structure returned during a call to OSGetIntlSettings. This argument is a void pointer to the INTLFORMAT.  Can be NULL, in which case this function invokes OSGetIntlSettings and works with those settings for the duration of this call.

TextFormat  -  A pointer to a TFMT structure -- which specifies the desired format of the character converted time/date string.  Can be NULL, in which case this function creates a temporary version of the required TFMT structure and assigns the following values to its members: 

td_format_ptr->Date = TDFMT_FULL;
td_format_ptr->Time = TTFMT_FULL;
td_format_ptr->Zone = TZFMT_NEVER;
td_format_ptr->Structure = TSFMT_DATETIME;


InputTime  -  A pointer to the Domino binary time/date structure that you want to convert.

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus one(1) or usually MAXALPHATIMEDATEPAIR.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - conversion successful. 
ERR_BUFFER_OVERFLOW - Output Buffer Overflow.
ERR_TDO_CONV - Invalid Time or Date Encountered.
ERR_IFMT - Invalid International Format Specifier.
ERR_TFMT - Invalid Time/Date Format Specifier.


retTextBuffer  -  The address of a text buffer in which the character text time/date result of the conversion is returned. The buffer must be declared with a length of (MAXALPHATIMEDATEPAIR) + 1.  This includes 1 for a future NULL terminator.  The returned text is not NULL terminated.

retTextLength  -  The address of a WORD in which the length of the converted character time/date pair text is returned.


**Sample Usage :**
```
  
   /* Convert Time/Date Pair to Text */
   binary_td_pair.Lower.Innards[0] = binary_td2.Innards[0];
   binary_td_pair.Lower.Innards[1] = binary_td2.Innards[1];
   binary_td_pair.Upper.Innards[0] = binary_td3.Innards[0];
   binary_td_pair.Upper.Innards[1] = binary_td3.Innards[1];
   td_string_ptr = &td_string_pair[0];
   if (error_status = ConvertTIMEDATEPAIRToText(&intl_format,
                                   &td_format, &binary_td_pair,
                                   td_string_ptr, MAXALPHATIMEDATEPAIR,
                                   &string_len))
       goto Exit;

```
**See Also :**
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/domino-c-api-docs/reference/Func/OSGetIntlSettings)
[TYPE_xxx [TIME_RANGE]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TIME_RANGE])
---
