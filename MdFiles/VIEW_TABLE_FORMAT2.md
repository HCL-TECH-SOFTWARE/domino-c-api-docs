




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



**VIEW\_TABLE\_FORMAT2** **-** Contains
additional view format information.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct {  

   WORD Length;             /\* Length of this structure \*/  

   WORD BackgroundColor;    /\* Color of view's background \*/  

   WORD V2BorderColor;      /\* Color of view's border lines \*/  

   FONTID TitleFont;        /\* Title and borders \*/  

   FONTID UnreadFont;       /\* Unread lines \*/  

   FONTID TotalsFont;       /\* Totals/Statistics \*/  

   WORD AutoUpdateSeconds;  /\* Interval b/w auto updates   

                               (zero for no autoupdate) \*/  

   WORD AlternateBackgroundColor; /\* Color of view's background for  

                                     alternate rows. \*/  

   WORD wSig;               /\* see VALID\_VIEW\_FORMAT\_SIG \*/  

  

   BYTE LineCount;          /\* Number of lines per row.  1, 2, etc.  

                               see VIEW\_TABLE\_MAX\_LINE\_COUNT \*/  

   BYTE Spacing;            /\* Spacing. see VIEW\_TABLE\_xxx\_SPACE \*/  

   WORD BackgroundColorExt; /\* Palette Color of view's background. \*/  

   BYTE HeaderLineCount;    /\* Lines per header. \*/  

   BYTE Flags1;            /\* see VIEW\_TABLE\_xxx \*/  

   WORD Spare[4];           /\* Spares.  Will be zero when


                                 
wSig == VALID\_VIEW\_FORMAT\_SIG. \*/  

} VIEW\_TABLE\_FORMAT2;


 


**Description :**



This
structure contains view format information for views saved in Notes 2.0 and
later. This structure is one of the components of a $VIEWFORMAT item in a view
note.  All view notes contain a $VIEWFORMAT item (also known as a "View
Table Format" item). A $VIEWFORMAT item is an item of TYPE\_VIEW\_FORMAT
with item name VIEW\_VIEW\_FORMAT\_ITEM. The item value of a $VIEWFORMAT item
consists of a single VIEW\_TABLE\_FORMAT structure, followed by one VIEW\_COLUMN\_FORMAT
structure for each column, followed by an  item name/formula/column title set
for each column, followed by a VIEW\_TABLE\_FORMAT2 structure, followed by one
VIEW\_COLUMN\_FORMAT2 structure for each column, followed by a VIEW\_TABLE\_FORMAT3
structure.


 **Sample Usage :**


  

VIEW\_TABLE\_FORMAT2     ViewTableFormat2;  

  

/\*  

 \* Initialize the VIEW\_TABLE\_FORMAT2 structure.  

 \*/  

memset (&ViewTableFormat2, 0, sizeof(VIEW\_TABLE\_FORMAT2));


  

ViewTableFormat2.Length = sizeof(VIEW\_TABLE\_FORMAT2);  

ViewTableFormat2.BackgroundColor = NOTES\_COLOR\_WHITE;  

ViewTableFormat2.V2BorderColor = 0;  

ViewTableFormat2.TitleFont = DEFAULT\_BOLD\_FONT\_ID;  

ViewTableFormat2.UnreadFont = DEFAULT\_FONT\_ID;  

ViewTableFormat2.TotalsFont = DEFAULT\_FONT\_ID;  

ViewTableFormat2.AutoUpdateSeconds = 0;  

  

/\*  

 \* Convert the View Table Format2 structure to Domino canonical  

 \* format and append it to the buffer. This increments pVFBuf to   

 \* point to the next byte after the View Table Format2 structure.  

 \*/  

  

ODSWriteMemory( &pVFBuf, \_VIEW\_TABLE\_FORMAT2, &ViewTableFormat2, 1 );  

  

/\*  

 \* Now append the View Table Format item to the note.  

 \*/  

  

sError = NSFItemAppend( hNote,  

                        ITEM\_SUMMARY,  

                        VIEW\_VIEW\_FORMAT\_ITEM,  

                        sizeof(VIEW\_VIEW\_FORMAT\_ITEM) - 1,  

                        TYPE\_VIEW\_FORMAT,  

                        pViewFormatBuffer,  

                        (DWORD)wViewFormatBufLen );


 **See Also :**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





