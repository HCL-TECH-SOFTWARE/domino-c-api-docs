




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




 


**Symbolic Value : Views**



**VIEW\_TABLE\_xxx (VIEW\_TABLE\_FORMAT)** **-** VIEW\_TABLE\_FORMAT
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VIEW\_TABLE\_FLAG\_COLLAPSED   -  View will default to fully
collapsed.  

  

      VIEW\_TABLE\_FLAG\_FLATINDEX    -  Do not index hierarchically If FALSE, the
'$REF' item must be LAST in the list of summary items for this view.  

  

      VIEW\_TABLE\_FLAG\_DISP\_ALLUNREAD     -  Display unread flags in margin at
ALL levels.  

  

      VIEW\_TABLE\_FLAG\_CONFLICT      -  Replication conflicts will be flagged.
If TRUE, the '$Conflict' item must be SECOND-TO-LAST in the list of summary
items for this view.  

  

      VIEW\_TABLE\_FLAG\_DISP\_UNREADDOCS              -  Display unread flags in
margin for documents only.  

  

      VIEW\_TABLE\_GOTO\_TOP\_ON\_OPEN        -  Position to top when view is
opened.  

  

      VIEW\_TABLE\_GOTO\_BOTTOM\_ON\_OPEN             -  Position to bottom when
view is opened.  

  

      VIEW\_TABLE\_ALTERNATE\_ROW\_COLORING        -  Color alternate rows.  

  

      VIEW\_TABLE\_HIDE\_HEADINGS      -  Hide headings.  

  

      VIEW\_TABLE\_HIDE\_LEFT\_MARGIN            -  Hide left margin.  

  

      VIEW\_TABLE\_SIMPLE\_HEADINGS              -  Show simple (background color)
headings.  

  

      VIEW\_TABLE\_VARIABLE\_LINE\_COUNT      -  TRUE if LineCount is variable (can
be reduced as needed).  

  

      VIEW\_TABLE\_GOTO\_TOP\_ON\_REFRESH   -  Position to top when view is
refreshed (as if the user pressed F9 and Ctrl-Home). When both
VIEW\_TABLE\_GOTO\_TOP\_ON\_REFRESH and VIEW\_TABLE\_GOTO\_BOTTOM\_ON\_REFRESH flags are
set, the view will be refreshed from the current top row (as if the user
pressed F9). When both flags are clear, automatic refresh of display on update
notification is disabled. In this case, the refresh indicator will be
displayed.  

  

      VIEW\_TABLE\_GOTO\_BOTTOM\_ON\_REFRESH      -  Position to bottom when view is
refreshed (as if the user pressed F9 and Ctrl-End). When both
VIEW\_TABLE\_GOTO\_TOP\_ON\_REFRESH and VIEW\_TABLE\_GOTO\_BOTTOM\_ON\_REFRESH flags are
set, the view will be refreshed from the current top row (as if the user
pressed F9). When both flags are clear, automatic refresh of display on update
notification is disabled. In this case, the refresh indicator will be
displayed.  

  

      VIEW\_TABLE\_EXTEND\_LAST\_COLUMN     -  TRUE if last column should be
extended to fit the window width.  

  

      VIEW\_TABLE\_RTLVIEW      -  TRUE if the View indexing should work from the
Right most column  

  




**Description :**



These flags
help define the format  used when a view is displayed. The Flags word of the
VIEW\_TABLE\_FORMAT structure contains a value constructed by combining these
flags using bitwise-OR.


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

  

ViewTableFormat.spare2 = 0;


 **See Also :**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





