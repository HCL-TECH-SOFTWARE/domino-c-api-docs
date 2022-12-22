




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




 


**Data Type : Address Book; Domino
Directory**



**LOOKUP\_MATCH** **-** Structure of
each record in the array of match buffers that are in the buffer returned from
NAMELookup.


**----------------------------------------------------------------------------------------------------------**



**#include
<lookup.h>**



**Definition :**



typedef struct {  

/\* WORD        Offset[NumItems];  \*\* Array of offsets from base of \*/  

                                  /\* LOOKUP\_MATCH structure to each \*/  

                                  /\* item value, in the same order \*/  

                                  /\* as the items were provided in \*/  

                                  /\* the request. \*/  

   WORD        Length;            /\* Length of LOOKUP\_MATCH buffer \*/  

                                  /\* Acts as Offset[N] array entry \*/  

                                  /\* so that to find the length of \*/  

                                  /\* any item, you can subtract \*/  

                                  /\* Offset[i+1] - Offset[i]. \*/  

/\* Item values (datatype and value)... \*/  

} LOOKUP\_MATCH;


 


**Description :**



Structure
which is returned for every matching record of a name in a call to NAMELookup. 
This structure appears immediately after the LOOKUP\_INFO structure.


 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[LOOKUP\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/47B0217741E89343852562070078CFA6)**



----------------------------------------------------------------------------------------------------------


 





