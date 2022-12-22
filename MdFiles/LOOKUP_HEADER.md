




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



**LOOKUP\_HEADER** **-** Structure of
the header of the buffer returned from NAMELookup.


**----------------------------------------------------------------------------------------------------------**



**#include
<lookup.h>**



**Definition :**



typedef struct {  

   WORD        Length;     /\* Length of entire buffer \*/  

   WORD        NumItems;   /\* # items returned with each match \*/  

/\* LOOKUP\_INFO NameInfo[NumNames]; \*\* Array of info for each name  

                                      looked up \*/  

} LOOKUP\_HEADER;


 


**Description :**



NAMELookup
returns a handle to a buffer containing name information. The buffer consists
of this header followed by a series of data records.


 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[LOOKUP\_INFO](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/47B0217741E89343852562070078CFA6)**



----------------------------------------------------------------------------------------------------------


 





