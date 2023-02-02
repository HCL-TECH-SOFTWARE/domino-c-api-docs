##### Function : Time
##### ConvertTextToTIMEDATEPAIR - Convert character time/date pair to TIMEDATE_PAIR.
---
##### #include <misc.h>
STATUS LNPUBLIC **ConvertTextToTIMEDATEPAIR(**

	const void far *IntlFormat,
	const TFMT far *TextFormat,
	char far * far *Text,
	WORD  MaxLength,
	TIMEDATE_PAIR far *retTIMEDATE);
**Description :**
This function converts a character time/date pair string into Domino binary 
TIMEDATE_PAIR format. 

You may also optionally request a non-standard format for the output string by 
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard "current" 
settings is acceptable.

The string syntax is: 1st_time/date_string + " - " + 2nd_time/date_string.  The 
two strings must not be identical, otherwise an error will be returned.

Please note that this "-" seperator is not neccessarily the same as the date 
seperator provided by OSGetIntlSettings.
**Parameters :**
Input :
IntlFormat  -  A pointer to a structure containing the internationalization settings in effect. You retrieve these settings in an INTLFORMAT structure by calling OSGetIntlSettings.  This must be done BEFORE calling ConvertTextToTIMEDATE.   Can be NULL, in which case this function invokes OSGetIntlSettings and works with those settings for the duration of this call.

TextFormat  -  A pointer to a TFMT structure -- which specifies the syntax of the date/time text string.   This structure must be populated by you before calling ConvertTextToTIMEDATE. See TDFMT_xxx, TTFMT_xxx, TZFMT_xxx, and TSFMT_xxx for an explanation of the definitions.   Can be NULL, in which case this function creates temporary version of the required TFMT structure and assigns the following values to its members: 

td_format_ptr->Date = TDFMT_FULL;
td_format_ptr->Time = TTFMT_FULL;
td_format_ptr->Zone = TZFMT_NEVER;
td_format_ptr->Structure = TSFMT_DATETIME;

Text  -  A pointer to a pointer to the character time/date pair string. This string should have a maximum length of (MAXALPHATIMEDATEPAIR) + 1.

MaxLength  -  The maximum number of significant characters in Text.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - conversion successful .
ERR_TDI_CONV - Unable to interpret Time or Date.
ERR_NOT_TDPAIR - TIMEDATE, not TIMEDATE_PAIR.
ERR_IFMT - Invalid International Format Specifier.
ERR_TFMT - Invalid Time/Date Format Specifier.


retTIMEDATE  -  The address of a TIMEDATE_PAIR structure in which the binary equivalent of the time/date pair text string is returned.

**Sample Usage :**
```

   td_string_ptr = &td_string_pair[0];
   if(error_status = ConvertTextToTIMEDATEPAIR(&intl_format,
                            &td_format, &td_string_ptr,
                            strlen(td_string_ptr), &binary_td_pair))
       goto Exit;

```
**See Also :**
[ConvertTIMEDATEPAIRToText](D:/md_files/ConvertTIMEDATEPAIRToText.md)
[OSCurrentTIMEDATE](D:/md_files/OSCurrentTIMEDATE.md)
[OSGetIntlSettings](D:/md_files/OSGetIntlSettings.md)
---
