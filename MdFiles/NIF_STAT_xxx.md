




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




 


**Symbolic Value : Views**



**NIF\_STAT\_xxx** **-** Description
of codes used in certain view note items.


**----------------------------------------------------------------------------------------------------------**



**#include <nifcoll.h>**


 **Symbolic Values :**      NIF\_STAT\_NONE     -  No subtotalling.  

  

      NIF\_STAT\_TOTAL   -  Total of values in subtree.  

  

      NIF\_STAT\_AVG\_PER\_CHILD           -  Total / # direct entries in parent's
index (1 level only below parent).  

  

      NIF\_STAT\_PCT\_OVERALL   -  Total / total of values in entire index.  

  

      NIF\_STAT\_PCT\_PARENT    -  Total / total of values in parent's index.  

  

      NIF\_STAT\_AVG\_PER\_ENTRY         -  Total / # descendants in parent's index
(all levels below parent).  

  

      NIF\_STAT\_AVERAGE          -  Obsolete symbol.  

  




**Description :**




In $Totals
view note item: 


      Use
these flags to specify whether/which subtotals are to be kept for each summary
buffer item. The $Totals item is a TYPE\_TEXT\_LIST item, where each member of
the text list is a string which can be converted into one of the following
codes by doing a "atoi" function on it. The order of the members of
the text list MUST MATCH the order of the entries in the summary buffer, even
if it means putting a blank string for a column which doesn't have any
totalling.  All of these statistics are kept in each subindex header, and apply
to all entries of that subindex AND ALL SUBINDEXES BELOW IT. 


 


In
$VIEWFORMAT view note item: 


      Use
these flags to set the SubtotalCode bits of the Flags2 member of a
VIEW\_COLUMN\_FORMAT structure. 


 


 **See Also :**


**[VCF2\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C5237445E8E3F894852564C3006F7A60)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





