




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




 


**Data Type : Views**



**VIEW\_TABLE\_FORMAT** **-** View table
format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct {  

   VIEW\_FORMAT\_HEADER Header;  

   WORD Columns;            /\* Number of columns \*/  

   WORD ItemSequenceNumber; /\* Seq. number for unique item names \*/  

   WORD Flags;              /\* (see VIEW\_TABLE\_xxx) \*/  

   WORD Flags2;             /\* Flags \*/  

} VIEW\_TABLE\_FORMAT;


 


**Description :**



This
structure contains the view table format descriptor.  All view notes contain a
$VIEWFORMAT item (also known as a "View Table Format" item). A
$VIEWFORMAT item is an item of TYPE\_VIEW\_FORMAT with item name
VIEW\_VIEW\_FORMAT\_ITEM. The item value of a $VIEWFORMAT item consists of a
single VIEW\_TABLE\_FORMAT structure, followed by one VIEW\_COLUMN\_FORMAT
structure for each column, followed by an  item name/formula/column title set
for each column, followed by a VIEW\_TABLE\_FORMAT2 structure, followed by one
VIEW\_COLUMN\_FORMAT2 structure for each column, followed by a VIEW\_TABLE\_FORMAT3
structure.


 **Sample Usage :**


/\*  

 Initialize the VIEW\_TABLE\_FORMAT structure.  

 \*/  

  

ViewTableFormat.Header.Version = VIEW\_FORMAT\_VERSION;  

ViewTableFormat.Header.ViewStyle = VIEW\_STYLE\_TABLE;  

ViewTableFormat.Columns = wNumColumns;  

ViewTableFormat.ItemSequenceNumber = 0;  /\* Reserved - should be 0 \*/  

      

ViewTableFormat.Flags = VIEW\_TABLE\_FLAG\_FLATINDEX |  

                        VIEW\_TABLE\_FLAG\_DISP\_UNREADDOCS;  

  

ViewTableFormat.Flags2 = VIEW\_TABLE\_FLAT\_HEADINGS;  

  

/\*  

 Call ODSWriteMemory to convert the VIEW\_TABLE\_FORMAT structure from  

 host-specific format to Domino canonical format, and copy it into the   

 buffer at location pVFBuf. ODSWriteMemory increments pVFBuf to point  

 to the next byte in the buffer after the written data structure.  

 \*/  

  

ODSWriteMemory( &pVFBuf, \_VIEW\_TABLE\_FORMAT, &ViewTableFormat, 1 );


 **See Also :**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_FORMAT\_HEADER](VIEW_FORMAT_HEADER.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**


**[VIEW\_TABLE\_xxx (VIEW\_TABLE\_FORMAT)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/000E008C00B1002685255E36005AD756)**


**[VIEW\_TABLE\_xxx (VIEW\_TABLE\_FORMAT)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/000E008C00B1002685255E36005AD756)**



----------------------------------------------------------------------------------------------------------


 





