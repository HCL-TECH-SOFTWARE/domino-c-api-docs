




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




**Initial Release 4.0**



**Data Type : Agents**



**ODS\_ASSISTRUNOBJECTHEADER** **-** Header for
objects added by an Agent.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   DWORD dwFlags;  /\* flags \*/  

   WORD  wEntries; /\* Number of entries following \*/  

   WORD  wSpare;


/\* entries follow \*/  

} ODS\_ASSISTRUNOBJECTHEADER;


 


**Description :**



When an
Agent is run, results may be generated and stored as objects following the
Agent.  The header contains the number of ODS\_ASSISTRUNOBJECTENTRY records that
follow.


 **See Also :**


**[ODS\_ASSISTRUNOBJECTENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7B9B64108B65382E85256261006341CE)**


**[ODS\_ASSISTSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/540A215A94BACC0385256261006222BC)**



----------------------------------------------------------------------------------------------------------


 





