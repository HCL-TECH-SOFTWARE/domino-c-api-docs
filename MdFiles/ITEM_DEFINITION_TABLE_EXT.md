




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0**



**Data Type : Item (Field) Information**



**ITEM\_DEFINITION\_TABLE\_EXT** **-** Database
Item Definition Table (Extended)


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef struct {  

   DWORD  Items;          /\* number of items in the table \*/  

   DWORD  ItemDefArray;   /\* Memory handle of ITEM\_DEFINITION\_EXT


                            
structures \*/  

   DWORD  NumSegments;    /\* Number of non-null segments in


                            
ItemNameSegs \*/  

   DHANDLE ItemNameSegs[MAX\_ITEMDEF\_SEGMENTS]; /\* Segments of


                             packed
text \*/  

   DWORD  ItemNameSegLengths[MAX\_ITEMDEF\_SEGMENTS]; /\* Length of


                            
each non-null text segment \*/  

} ITEM\_DEFINITION\_TABLE\_EXT;


 


**Description :**



This table
contains extended information for all the items defined in a database.   The
fields in the structure are:


 


Items                                                                                  The
number of items in the table


ItemDefArray                                                                      Memory
handle of ITEM\_DEFINITION\_EXT structures


NumSegments                                                                    Number
of non-null segments of packed text.


ItemNameSegs[MAX\_ITEMDEF\_SEGMENTS]                    An
array of handles to non-null segments of packed text.


ItemNameSegLengths[MAX\_ITEMDEF\_SEGMENTS]          Length
of each non-null text segment.


 


Use the
following NSF functions to extract data from this structure:


NSFItemDefExtEntries,
NSFItemDefExtGetEntry.


 


 **See Also :**


**[ITEM\_DEFINITION\_EXT](ITEM_DEFINITION_EXT.md)**


**[ITEM\_DEFINITION\_TABLE\_LOCK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/901659ECD32C4D5185256711004FD3A8)**


**[NSFDbItemDefTableExt](NSFDbItemDefTableExt.md)**


**[NSFItemDefExtEntries](NSFItemDefExtEntries.md)**


**[NSFItemDefExtFree](NSFItemDefExtFree.md)**


**[NSFItemDefExtGetEntry](NSFItemDefExtGetEntry.md)**


**[NSFItemDefExtLock](NSFItemDefExtLock.md)**


**[NSFItemDefExtUnlock](NSFItemDefExtUnlock.md)**



----------------------------------------------------------------------------------------------------------


 





