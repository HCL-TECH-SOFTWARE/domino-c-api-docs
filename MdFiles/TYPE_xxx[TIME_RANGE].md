




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Symbolic Value : Item (Field)
Information**



**TYPE\_xxx [TIME\_RANGE]** **-** Item Data
Type - Time/Date List/Range


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



Time/Date
List or Range fields contains two or more Time/Date values and/or zero or more
ranges of Time/Date values. Time/Date List or Range fields are stored in notes
as items of TYPE\_TIME\_RANGE.   

  

An item of TYPE\_TIME\_RANGE consists of a range header, an array of TIMEDATEs,
and an array of TIMEDATE\_PAIRs, as follows:  

  




   RANGE          range
header  

   TIMEDATE       time/date no. 0  

   TIMEDATE       time/date no. 1  

   ...  

   TIMEDATE       time/date no. N  

   TIMEDATE\_PAIR  time/date range no. 0  

   TIMEDATE\_PAIR  time/date range no. 1  

   ...  

   TIMEDATE\_PAIR  time/date range no. N  

  

The ListEntries member of the range header contains the number of TIMEDATEs in
the array of TIMEDATEs.  The RangeEntries member of the range header contains
the number of TIMEDATE\_PAIRs in the array of TIMEDATE\_PAIRs.  

  

To create a Time/Date List or Range field using the API, initialize a RANGE
structure, any number of TIMEDATE structures, and any number of TIMEDATE\_PAIR
structures. Initialize a memory buffer with the RANGE structure, followed by
all the TIMEDATE structures, followed by all the TIMEDATE\_PAIR structures. Then
call NSFItemAppend to append this buffer to an open note.  

  

The total length of a Time/Date List or Range field must not exceed 15
kilobytes.  

  

To create a Time/Date List or Range field using the Notes user interface,
compose a document using a form with a Time field that accepts multiple values.
Enter two or more time/date values, separated by multi-value separators, into
the field. The Time field accepts multiple values if the design of the field in
the form has the Allow Multi-Value box checked in the Field Definition dialog
box. The multi-value separators are also defined by the design of the field in
the form. The default multi-value separators for Time fields are commas and
semicolons. The multi-value separators are not stored in the field.  

  

For Time/Date List or Range fields created using the Notes user interface, the
SUMMARY flag is set by default. For Time/Date List or Range fields created
using the API, specify ITEM\_SUMMARY in the item\_flags parameter of
NSFItemAppend to set the SUMMARY flag.


 **Sample Usage :**


NOTEHANDLE     hNote;  

char          \*szFieldName;  

TIMEDATE      \*aTimeDates;  

WORD           usCount;  

DWORD          dwValueLen;  

void far      \*pvoidItemValue;  

RANGE         \*pRange;  

TIMEDATE      \*pTimeDate;  

WORD           i;  

STATUS         error;  

  

dwValueLen = sizeof(RANGE) + (usCount \* sizeof(TIMEDATE));  

pvoidItemValue = (void far \*) malloc ((size\_t)dwValueLen);  

  

pRange = (RANGE\*)pvoidItemValue;  

pRange->ListEntries = usCount;  

pRange->RangeEntries = 0;  

pRange++;  

pTimeDate = (TIMEDATE\*)pRange;  

  

for (i = 0; i < usCount; i++)  

{  

    \*pTimeDate = aTimeDates[i];  

    pTimeDate++;  

}  

      

error = NSFItemAppend (hNote, ITEM\_SUMMARY,  

                szFieldName, strlen(szFieldName),  

                TYPE\_TIME\_RANGE,  

                pvoidItemValue, dwValueLen);  

  

free (pvoidItemValue);


 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTextToTIMEDATEPAIR](ConvertTextToTIMEDATEPAIR.md)**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[RANGE](RANGE.md)**


**[TIMEDATE](TIMEDATE.md)**


**[TIMEDATE\_PAIR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/008C0090007D00EA85255E2D00792E78)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





