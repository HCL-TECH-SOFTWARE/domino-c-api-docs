##### Function : Number
##### ConvertFLOATToText - Converts a FLOAT to a character text string.
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertFLOATToText(

	const void far *IntlFormat,
	const NFMT far *NumberFormat,
	NUMBER far *Number,
	char far *retTextBuffer,
	WORD  TextBufferLength,
	Word far *retTextLength);
```
**Description :**

This function converts a floating point number (NUMBER) to a character text 
string.

You may also optionally request a nonstandard format for the number string by 
setting up an NFMT and/or an INTLFORMAT structure.  Use NULL if the standard 
"current" settings are  acceptable.

**Parameters :**
Input :
IntlFormat  -  A pointer to a structure containing the internationalization settings in effect. You retrieve these settings in an INTLFORMAT structure by calling OSGetIntlSettings.  This must be done BEFORE calling ConverFLOATToText.  Can be NULL, in which case this function invokes OSGetIntlSettings and works with those settings for the duration of the call.

NumberFormat  -  A pointer to an NFMT structure -- which specifies the format and attributes of the number text string.   This structure must be populated by you before calling ConvertFLOATToText. See NFMT_xxx, NATTR_xxx for an explanation of the definitions.   Can be NULL, in which case this function creates a default NFMT structure with the following settings:

NumberFormat->Digits = 2;
NumberFormat->Format = NFMT_GENERAL;
NumberFormat->Attributes = 0;

Number  -  A pointer to the FLOAT that is to be converted. 

retTextBuffer  -  A pointer to a text buffer in which to return the text string.  The buffer should be at least MAXALPHANUMBER + 1 bytes in length.

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus one (1).  Since it is recommended that the buffer be of size MAXALPHANUMBER + 1, this is usually MAXALPHANUMBER.

retTextLength  -  The address of a WORD in which the length of the resulting text string will be returned.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - Conversion successful. 
ERR_IFMT - Invalid International Format Specifier.
ERR_NFMT - Invalid Number Format Specifier.


retTextBuffer  -  A pointer to the resulting character text NUMBER string.

retTextLength  -  The address of a WORD containing the length of the resulting text string.


**Sample Usage :**
```
  if (sError = ConvertFLOATToText(NULL,
                                   NULL,
                                   &retNumber,
                                   OutputText,
                                   sizeof(OutputText),
                                   &retTextLen))
   {
    return (ERR(sError));
   }                            

```
**See Also :**
[ConvertTextToFLOAT](/domino-c-api-docs/reference/Func/ConvertTextToFLOAT)
[OSGetIntlSettings](/domino-c-api-docs/reference/Func/OSGetIntlSettings)
---
