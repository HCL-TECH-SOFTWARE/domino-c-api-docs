




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



**Data Type : Agents; Composite Data**



**CDACTIONREADMARKS** **-** Modify Read
Marks action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   BSIG  Header;  

   DWORD dwFlags;  

} CDACTIONREADMARKS;


 


**Description :**



This action
CD record is stored in the TYPE\_ACTION field of an Agent.  When this action
record is encountered, the unread marks for the documents selected by the query
segment of the Agent will either be set to Read (if the signature is
SIG\_ACTION\_MARKREAD) or Unread (if the signature is SIG\_ACTION\_MARKUNREAD).


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





