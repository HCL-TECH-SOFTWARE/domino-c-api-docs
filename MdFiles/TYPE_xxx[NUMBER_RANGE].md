




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



**TYPE\_xxx [NUMBER\_RANGE]** **-** Item Data
Type - Number List/Range


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



Number List
fields contain one or more numbers. They are stored in notes as items of
TYPE\_NUMBER\_RANGE.  An item of TYPE\_NUMBER\_RANGE consists of a range header
followed by an array of numbers, as follows:  

RANGE         range header  

NUMBER        number no. 0  

NUMBER        number no. 1  

...  

NUMBER        number no. N  

  

  

The range header is a RANGE data structure. The ListEntries member of the
header is a USHORT that contains the number of NUMBERs in the list. Since
ranges of numbers are not supported in Domino, the RangeEntries member of the
header should be set to 0.   

  

After the header comes an array of NUMBERs. There are ListEntries NUMBERSs in
the array.  

  

In the Notes user interface, create a Number List field by composing a document
using a form with a Number field that accepts multiple values. Enter one or
more numbers, separated by multi-value separators, into the field. The Number
field accepts multiple values if the design of the field in the form has the
Allow Multi-Values box checked in the Field Definition dialog box. The
multi-value separators are also defined by the design of the field in the form.
The default multi-value separator for Number fields is a comma or a semicolon,
but others may be used.   

  

To create a number list field from the API, allocate a block of memory
sufficient to hold a RANGE data structure followed by as many NUMBERs as you
need. Initialize a RANGE structure, then append it to the memory block. Append
NUMBERs to the memory block following the RANGE. Finally, call NSFItemAppend
specifying the memory block as the item value. Specify data type
TYPE\_NUMBER\_RANGE. Domino and Notes automatically convert  items of type
TYPE\_NUMBER\_RANGE to canonical format when appending them to a note, and
convert them to host format when reading them from a note. Therefore, do not
perform host/canonical conversion on this data.  

  

The multi-value separator character is not stored in the number list field.   

  

The total length of a Number List field must not exceed 15 kilobytes.   

  

For Number List fields created using the Notes user interface, the SUMMARY flag
is set by default. For Number List fields created using the API, specify
ITEM\_SUMMARY in the item\_flags parameter of NSFItemAppend to set the SUMMARY
flag.


 **Sample Usage :**


#define LIST\_COUNT 5  

  

DBHANDLE    hDB;  

NOTEHANDLE  hNote;  

DWORD       dwValueLen;  

void far   \*pvoidItemValue;  

RANGE      \*pRange;  

NUMBER     \*pNumber;  

WORD        i;  

STATUS      error;  

NUMBER      aNumbers[LIST\_COUNT] = {1,3,9703.4,-7,0.11592};  

  

dwValueLen = sizeof(RANGE) + (LIST\_COUNT \* sizeof(NUMBER));  

pvoidItemValue = (void far \*) malloc ((size\_t)dwValueLen);  

  

pRange = (RANGE\*)pvoidItemValue;  

pRange->ListEntries = usCount;  

pRange->RangeEntries = 0;  

pRange++;  

pNumber = (NUMBER\*)pRange;  

  

for (i = 0; i < LIST\_COUNT; i++)  

{  

    \*pNumber = aNumbers[i];  

    pNumber++;  

}  

  

error = NSFItemAppend (hNote,   

            ITEM\_SUMMARY,  

            szFieldName,   

            strlen(szFieldName),  

            TYPE\_NUMBER\_RANGE,  

            pvoidItemValue,   

            dwValueLen);  

  

free (pvoidItemValue);


 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NUMBER](NUMBER.md)**


**[RANGE](RANGE.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





