




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



**TYPE\_xxx [TEXT\_LIST]** **-** Item Data
Type - Text List


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



Text List
fields contain one or more text strings. They are stored in notes as items of
TYPE\_TEXT\_LIST.  An item of TYPE\_TEXT\_LIST consists of a list header, an array
of text string lengths, and a packed series of text strings, as follows:  

LIST         list header  

USHORT       length of string 0  

USHORT       length of string 1  

...            

USHORT       length of string N  

text         text of string 0  

text         text of string 1  

...  

text         text of string N  

Create a Text List field by calling the function NSFItemCreateTextList. Append
additional text strings by calling the function NSFItemAppendTextList. Read a
single text string in a Text List by calling the function
NSFItemGetTextListEntry. Determine the number of strings in the list by calling
NSFItemGetTextListEntries.  

  

The list header is a LIST data structure. The ListEntries member of the header
contains the number of strings in the list. After the header comes an array of
lengths. There are ListEntries lengths in this array. Each length in the array
contains the text length of the corresponding string. After the lengths array
comes the packed text for all the strings. There are ListEntries strings. There
are no separators between the strings, and the strings may contain embedded
NULL characters.   

  

 In the Notes user interface, create a Text List field by composing a document
using a form with a Text field. Enter two or more strings, separated by
multi-value separators, into the text field. The multi-value separators for a
given field are defined in the design of that field in the form. The default
multi-value separator is a comma but others, such as semicolon, may be used.
The multi-value separator character is not stored in the text list field.  

  

The total length of a Text List field must not exceed 15 kilobytes. By default,
the SUMMARY flag is set for Text List fields.


 **Sample Usage :**


NSFItemCreateTextList (
note\_handle,  

                        "Categories",  

                        "Manufacturing",  

                         MAXWORD);  

  

NSFItemAppendTextList ( note\_handle,   

                       "Categories",  

                       "Operations",   

                        MAXWORD, TRUE);


 **See Also :**


**[LIST](LIST.md)**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetSize](ListGetSize.md)**


**[ListGetText](ListGetText.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**


**[NSFItemAppendTextList](NSFItemAppendTextList.md)**


**[NSFItemCreateTextList](NSFItemCreateTextList.md)**


**[NSFItemGetTextListEntries](NSFItemGetTextListEntries.md)**


**[NSFItemGetTextListEntry](NSFItemGetTextListEntry.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





