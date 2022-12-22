




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



**LOOKUP\_INFO** **-** Structure of
the data records that are in the buffer returned from NAMELookup.


**----------------------------------------------------------------------------------------------------------**



**#include
<lookup.h>**



**Definition :**



typedef struct {  

   WORD         NumMatches;       /\* # records which match the name \*/  

/\* LOOKUP\_MATCH Matches[NumMatches];   \*\* Array of match buffers... \*/  

} LOOKUP\_INFO;


 


**Description :**



NAMELookup
returns a handle to a buffer containing name information. The buffer consists
of a header (LOOKUP\_HEADER) followed by a series LOOKUP\_INFO structures  The
order of the LOOKUP\_INFO structures correspond to the order of names specified
in the Names parameter of the call to NAMELookup.  Each LOOKUP\_INFO structure
is followed by an array of LOOKUP\_MATCH structures.


 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[LOOKUP\_HEADER](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E3EB5BA15F9C8AD08525620700785B20)**



----------------------------------------------------------------------------------------------------------


 





