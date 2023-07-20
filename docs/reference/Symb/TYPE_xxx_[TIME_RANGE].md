##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [TIME_RANGE] - Item Data Type - Time/Date List/Range
---
```
#include <nsfdata.h>
```

**Symbolic Values :**



**Description :**

Time/Date List or Range fields contains two or more Time/Date values and/or zero or more ranges of Time/Date values. Time/Date List or Range fields are stored in notes as items of TYPE_TIME_RANGE. <br>
<br>
An item of TYPE_TIME_RANGE consists of a range header, an array of TIMEDATEs, and an array of TIMEDATE_PAIRs, as follows:<br>

<ul><br>
<tt><font size="2">&nbsp; &nbsp;RANGE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;range header<br>
 &nbsp; TIMEDATE &nbsp; &nbsp; &nbsp; time/date no. 0<br>
 &nbsp; TIMEDATE &nbsp; &nbsp; &nbsp; time/date no. 1<br>
 &nbsp; ...<br>
 &nbsp; TIMEDATE &nbsp; &nbsp; &nbsp; time/date no. N<br>
 &nbsp; TIMEDATE_PAIR &nbsp;time/date range no. 0<br>
 &nbsp; TIMEDATE_PAIR &nbsp;time/date range no. 1<br>
 &nbsp; ...<br>
 &nbsp; TIMEDATE_PAIR &nbsp;time/date range no. N</font></tt><br>
<br>
The ListEntries member of the range header contains the number of TIMEDATEs in the array of TIMEDATEs.  The RangeEntries member of the range header contains the number of TIMEDATE_PAIRs in the array of TIMEDATE_PAIRs.<br>
<br>
To create a Time/Date List or Range field using the API, initialize a RANGE structure, any number of TIMEDATE structures, and any number of TIMEDATE_PAIR structures. Initialize a memory buffer with the RANGE structure, followed by all the TIMEDATE structures, followed by all the TIMEDATE_PAIR structures. Then call NSFItemAppend to append this buffer to an open note.<br>
<br>
The total length of a Time/Date List or Range field must not exceed 15 kilobytes.<br>
<br>
To create a Time/Date List or Range field using the Notes user interface, compose a document using a form with a Time field that accepts multiple values. Enter two or more time/date values, separated by multi-value separators, into the field. The Time field accepts multiple values if the design of the field in the form has the Allow Multi-Value box checked in the Field Definition dialog box. The multi-value separators are also defined by the design of the field in the form. The default multi-value separators for Time fields are commas and semicolons. The multi-value separators are not stored in the field.<br>
<br>
For Time/Date List or Range fields created using the Notes user interface, the SUMMARY flag is set by default. For Time/Date List or Range fields created using the API, specify ITEM_SUMMARY in the item_flags parameter of NSFItemAppend to set the SUMMARY flag.</ul>



**Sample Usage :**
```
NOTEHANDLE     hNote;
char          *szFieldName;
TIMEDATE      *aTimeDates;
WORD           usCount;
DWORD          dwValueLen;
void far      *pvoidItemValue;
RANGE         *pRange;
TIMEDATE      *pTimeDate;
WORD           i;
STATUS         error;

dwValueLen = sizeof(RANGE) + (usCount * sizeof(TIMEDATE));
pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);

pRange = (RANGE*)pvoidItemValue;
pRange->ListEntries = usCount;
pRange->RangeEntries = 0;
pRange++;
pTimeDate = (TIMEDATE*)pRange;

for (i = 0; i < usCount; i++)
{
    *pTimeDate = aTimeDates[i];
    pTimeDate++;
}
    
error = NSFItemAppend (hNote, ITEM_SUMMARY,
                szFieldName, strlen(szFieldName),
                TYPE_TIME_RANGE,
                pvoidItemValue, dwValueLen);

free (pvoidItemValue);
```

**See Also :**
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
[ConvertTIMEDATEPAIRToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEPAIRToText)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[RANGE](/domino-c-api-docs/reference/Data/RANGE)
[TIMEDATE](/domino-c-api-docs/reference/Data/TIMEDATE)
[TIMEDATE_PAIR](/domino-c-api-docs/reference/Data/TIMEDATE_PAIR)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
