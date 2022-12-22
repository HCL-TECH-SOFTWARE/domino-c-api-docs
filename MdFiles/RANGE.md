




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




 


**Data Type : Item (Field) Information**



**RANGE** **-** Used to
specify multiple values in a data field.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



typedef struct {  

   USHORT ListEntries;  

   USHORT RangeEntries;  

/\* now come the list entries \*/  

/\* now come the range entries \*/  

  

} RANGE;


 


**Description :**



This
structure is used to specify a data field that contains more than one value. 
There are two ways to specify multiple values in a data field:  a list of
values or a range of values.  A list is made up of one or more items of a
datatype, separated by a delimiter.  A range is made up of consecutive data
given the start and end of the data.  Note that not all datatypes support both
lists and ranges.  

  

The value in the ListEntries field of RANGE is the number of items specified in
a delimited list of items.  

  

The value in the RangeEntries field of RANGE is the number of item pairs
specified as ranges.  

  




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


**[TYPE\_xxx [NUMBER\_RANGE]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/35ABE18F9580CA2D8525622E0062C48D)**


**[TYPE\_xxx [TIME\_RANGE]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C598A7AE1C5A2C6A8525622E00645C02)**



----------------------------------------------------------------------------------------------------------


 





