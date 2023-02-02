##### Function : TIMEDATE
##### ConvertRFC3339DateToTIMEDATE - Converts a date/time string of RFC3339 format to Notes TimeDate format.
---
##### #include <misc.h>
STATUS **ConvertRFC3339DateToTIMEDATE(**

	char far * far *RFC3339Date,
	WORD  MaxLength,
	BOOL  bDST,
	TIMEDATE*ptdTimeDate);
**Description :**
This routine converts Notes TIMEDATE structure to RFC3339 Date formatted text 
string, such as the following:
"YYYY-MM-DDTHH:MM:SS.hhZ (i.e., 1985-04-12T23:20:50.52Z)"
The routine does argument checking. The input Notes time/date string is 
MAXSPRINF long and NULL terminated to protect against a non-null terminated 
input string and buffer overflow.
**Parameters :**
Input :
RFC3339Date  -  A pointer to a RFC 3339 date&time string .

MaxLength  -  Maximum parsing length for RFC3339Date string.

bDST  -  Set DST flag in the result.

Output :
(routine)  -  On invalid syntax, ERR_TDI_CONV error is returned, on successful conversion returns NOERROR.


ptdTimeDate  -  Pointer to Notes Time/date populated from this function.

**Sample Usage :**
```
char rfc3339Date[STRING_LENGTH] = { 0 };
char timeDateBuf[STRING_LENGTH] = { 0 }; 
TIMEDATE td = { 0 };
char *pcrfc3339Date = (char*) rfc3339Date;
time_t rawtime;
/* Populate RFC3339 from gmtime */
strftime(rfc3339Date, sizeof(rfc3339Date), "%Y-%m-%dT%T", localtime(&rawtime));

/* Get the Zone from gmtime */
strftime(sZone, sizeof(sZone), "%z", localtime(&rawtime));

/* Format the RFC specific date time */
if (!strncmp(SubString(sZone, subStr2, 1, 3), "+00", strlen("+00")) && 
!strncmp(SubString(sZone, subStr, 4, 2), "00", strlen("00")))
{
sprintf(rfc3339Date,"%sZ", rfc3339Date);
}
else
{
sprintf(rfc3339Date,"%s%s:%s", rfc3339Date, SubString(sZone, subStr2, 1, 3), 
SubString(sZone, subStr, 4, 2));
}

/* Convert Text Range to Internal TIMEDATE pair */
sError = ConvertRFC3339DateToTIMEDATE(&pcrfc3339Date,
(WORD)strlen(rfc3339Date),
FALSE,
&td);
if (sError == NOERROR)
   printf("\n Error in convert");

```
**See Also :**
[](D:/md_files/.md)
---
