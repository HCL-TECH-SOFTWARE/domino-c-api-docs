




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.0**



**Symbolic Value : Search**



**PERCENTILE\_xxx** **-** Indices into
percentile key table


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      PERCENTILE\_0       -  0: Table entry for first key in
collection  

  

      PERCENTILE\_10      -  1: Table entry for first 1/10 of collection  

  

      PERCENTILE\_20      -  2: Table entry for second 1/10 of collection  

  

      PERCENTILE\_30      -  3: Table entry for third 1/10 of collection  

  

      PERCENTILE\_40      -  4: Table entry for fourth 1/10 of collection  

  

      PERCENTILE\_50      -  5: Table entry for the first half of a collection  

  

      PERCENTILE\_60      -  6: Table entry for sixth 1/10 of collection  

  

      PERCENTILE\_70      -  7: Table entry for seventh 1/10 of collection  

  

      PERCENTILE\_80      -  8: Table entry for eighth 1/10 of collection  

  

      PERCENTILE\_90      -  9: Table entry for ninth 1/10 of collection 1/10 of
collection  

  

      PERCENTILE\_100    -  10: Table entry for last key in collection  

  




**Description :**



Keys in a
COLLECTIONDATA structure are divided into percentiles - divisions corresponding
to one-tenth of the total range of keys - and a table of the keys marking the
divisions is returned with that structure.  These constants are provided for
indexing into the table.


 **See Also :**


**[COLLECTIONDATA](COLLECTIONDATA.md)**


**[PERCENTILE\_COUNT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3071BA559D3650D285256224004558D3)**



----------------------------------------------------------------------------------------------------------


 





