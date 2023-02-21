##### Function : Time
##### OSGetIntlSettings - Get international settings.
---
```
#include <intl.h>
void LNPUBLIC OSGetIntlSettings(

	INTLFORMAT far *retIntlFormat,
	WORD  BufferSize);
```
**Description :**

Domino and Notes maintain a table of International format information 
independent of the host operating environment.  This table contains currency 
and date formatting information.

The INTLFORMAT structure is a parameter to several of the date and time 
conversion functions. OSGetIntlSettings should be called prior to the calling 
of any of these functions to initialize a local copy of the structure prior to 
tailoring it to the desired options.

If the program does not require tailored formats, use NULL as the address of 
the INTLFORMAT structure to functions such as ConvertTIMEDATEToText instead of 
calling this function, since a NULL argument to those functions is defined to 
mean the "current international settings".

**Parameters :**
Input :

BufferSize  -  Size of the INTLFORMAT structure pointed to by the intl_format parameter.  OSGetIntlSettings will fill in the Length field of the specified INTLFORMAT structure  with this buffer size.  This allows API programs that use OSGetIntlSettings to be compatible with future versions of Domino and Notes.

Output :
(routine)  -  None.


retIntlFormat  -  The address of an INTLFORMAT structure in which the current international settings are returned.  This structure is now ready for use with TIMEDATE conversion routines or in conjunction with any user defined functions that parse time, date, or currency strings.


**Sample Usage :**
```

   /* Obtain International Settings, local TimeZone, and local */
   /* Daylight Savings Time status.                            */

   OSGetIntlSettings(&intl_format, sizeof(intl_format));

```
**See Also :**
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[INTLFORMAT](/domino-c-api-docs/reference/Data/INTLFORMAT)
---
