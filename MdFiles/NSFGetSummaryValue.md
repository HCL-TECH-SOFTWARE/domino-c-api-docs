




<!--
 /\* Font Definitions \*/
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




 


**Function : Item (Field)**



**NSFGetSummaryValue** **- Get a
text item value from a Summary Buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFGetSummaryValue(**  

      const void far \*summary\_buffer\_ptr,  

      const char far \*text\_item\_name,  

      char far \*text\_item\_value,  

      WORD  max\_buffer\_len**);**



**Description :**



This
function obtains a text item's value from a Summary Buffer and as such, is a
simplified form of NSFLocateSummaryValue().  A Summary Buffer is an ITEM\_TABLE
containing some of the items associated with a note and this function allows
you to easily access TYPE\_TEXT items.  

  

If an item was added to the note with the ITEM\_SUMMARY bit set in the ItemFlags
argument of NSFItemAppend, then it is an item which can be returned in a
Summary Buffer.  Summary Buffers are returned by functions such as
NIFReadEntries() and NSFSearch().  

  

Note:  the names and values of all items that have their ITEM\_SUMMARY item flag
set can be used in formulas and can therefore be displayed in a View.  If an
item is not marked with the ITEM\_SUMMARY flag, it cannot be used in a view, nor
will be returned in the Summary Buffer that is returned by NSFSearch().


 


**Parameters :**



Input :  

summary\_buffer\_ptr  -  A pointer to a summary buffer (ITEM\_TABLE).  

  

text\_item\_name  -  A pointer to a null-terminated item name whose value you
want to obtain.  

  

max\_buffer\_len  -  A WORD containing the total length of the buffer provided
for this call.  

  




Output :  

(routine)  -  On Return from this call -  

  

TRUE - Item was found.  

FALSE - Item was NOT found.  

  

  

text\_item\_value  -  The address of text buffer in which the null-terminated
string value obtained from the summary buffer is returned.  

  




 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFLocateSummaryValue](NSFLocateSummaryValue.md)**


**[NSFSearch](NSFSearch.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





