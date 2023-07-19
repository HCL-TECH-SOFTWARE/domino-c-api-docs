##### Data Type : Time
##### INTLFORMAT - Holds country and workstation settings.
---
```
#include <intl.h>
```

**Definition :**

typedef struct {
   WORD Flags;                   /* OR'd #defines for daylight
                                    savings, number, time, and date
                                    formats - see Symbolic Values
                                    CLOCK_24_HOUR, CURRENCY_SPACE,
                                    CURRENCY_SUFFIX, DATE_DMY,
                                    DATE_MDY, DATE_YMD,
                                    DAYLIGHT_SAVINGS,
                                    NUMBER_LEADING_ZERO */
   BYTE CurrencyDigits;          /* Number of decimal digits in
                                    fractional monetary amounts */
   BYTE Length;                  /* Length of this structure */
                                    If this structure is set from
                                    scratch, THIS MUST BE SET TO
                                    THE EXACT SIZE OF THE STRUCTURE
                                    WHEN ITS POINTER IS PASSED AS
                                    AN ARGUMENT */
   int  TimeZone;                /* number of hours added to the time
	        to get Greenwich Mean Time. May be 
	        positive or negative. */
   char AMString[ISTRMAX];       /* AM/am string used in countries
                                    with 12 hour time format */
   char PMString[ISTRMAX];       /* PM/pm string used in countries
                                    with 12 hour time format */
   char CurrencyString[ISTRMAX]; /* Symbol for currency:
                                    $, Fr, SEK, etc.  */
   char ThousandString[ISTRMAX]; /* Symbol formatting monetary
                                    amounts in thousands  */
   char DecimalString[ISTRMAX];  /* Symbol denoting decimal
                                    fraction of monetary amounts */
   char DateString[ISTRMAX];     /* Character(s) separating
                                    components of date string */
   char TimeString[ISTRMAX];     /* Character(s) separating
                                    components of time string */
   char YesterdayString[YTSTRMAX]; /* String denoting previous
                                    day */
   char TodayString[YTSTRMAX];   /* String denoting current day */
   char TomorrowString[YTSTRMAX];
} INTLFORMAT;

**Description :**

The INTLFORMAT typedef is used to declare a data structure that is returned from OSGetIntlSettings with country and workstation dependant information.  This structure provides information useful in parsing or composing Time, Date, and Currency strings.  It is also used by ConvertTextToTIMEDATE and ConvertTIMEDATEToText to indicate the expected or resulting string format, current time zone and daylight savings values.<br>

<ul>Note: The function ConvertTIMEDATEToText does not take the DAYLIGHT_SAVINGS flag  into account.</ul>



**See Also :**
[CLOCK_24_HOUR](/domino-c-api-docs/reference/Symb/CLOCK_24_HOUR)
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[CURRENCY_SPACE](/domino-c-api-docs/reference/Symb/CURRENCY_SPACE)
[CURRENCY_SUFFIX](/domino-c-api-docs/reference/Symb/CURRENCY_SUFFIX)
[DATE_DMY](/domino-c-api-docs/reference/Symb/DATE_DMY)
[DATE_MDY](/domino-c-api-docs/reference/Symb/DATE_MDY)
[DATE_YMD](/domino-c-api-docs/reference/Symb/DATE_YMD)
[DAYLIGHT_SAVINGS](/domino-c-api-docs/reference/Symb/DAYLIGHT_SAVINGS)
[NUMBER_LEADING_ZERO](/domino-c-api-docs/reference/Symb/NUMBER_LEADING_ZERO)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/domino-c-api-docs/reference/Func/OSGetIntlSettings)
---
