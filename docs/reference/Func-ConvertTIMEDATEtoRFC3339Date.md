##### Function : TIMEDATE
##### ConvertTIMEDATEtoRFC3339Date - Converts a time/date string of Notes TimeDate format to RFC3339 format. 
---
##### #include <misc.h>
STATUS **ConvertTIMEDATEtoRFC3339Date(**

	const TIMEDATE far *ptdTimeDate,
	WORD  wTextBufSize,
	char *pachText);
**Description :**
This routine converts Notes TIMEDATE structureto RFC3339 Date formatted text 
string, such as the following:
"YYYY-MM-DDTHH:MM:SS.hhZ (i.e., 1985-04-12T23:20:50.52Z) 
The routine does argument checking. The input Notes time/date string is 
MAXSPRINF long and NULL terminated to protect against a non-null terminated 
input string and buffer overflow.”
**Parameters :**
Input :
ptdTimeDate  -  A pointer to a Notes time/date string .

wTextBufSize  -  String Buffer Size. Big enough to inlude the trailing null char.

Output :
(routine)  -  On invalid syntax, ERR_TDI_CONV error is returned, on successful conversion returns NOERROR. 


pachText  -  A pointer to string buffer for ASCII string

**Sample Usage :**
```
#define TEXTBUFSIZE 256

TIMEDATE tdNowTime;
OSCurrentTIMEDATE(&tdNowTime);
char textBuffer[MAXSPRINTF] = {0};
if (error = ConvertTIMEDATEtoRFC3339Date(&tdNowTime,textBuffer,TEXTBUFSIZE)){
PRINTLOG( "Error in converting TIMEDATE to RFC339 TIMEDATE\n");
}
else {
PRINTLOG("RFC339 TIMEDATE = %s\n",textBuffer);
PRINTLOG("Successfully converted Notes TIMEDATE to RFC339 TIMEDATE.\n");
}
```
**See Also :**
[](D:/md_files/.md)
---
