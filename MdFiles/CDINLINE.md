




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




**Initial Release 6**



**Data Type : Composite Data; Rich
Text**



**CDINLINE** **-** Pertains to
shared resources and/or shared code in a form.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      WSIG Header;  

      WORD wDatalength;  

      DWORD dwFlags;  

      DWORD dwReserved[4];  

      } CDINLINE;


 


 


**Description :**



This CD
Record gives information pertaining to shared resources and/or shared code in a
form.  A CDINLINE record may be preceded by a CDBEGINRECORD and followed by a
CDRESOURCE and then a CDENDRECORD.  The fields in this record are:


 


Header -
Signature and Length of this CD record.


wDatalength
- Reserved for future use. Must be zero. 


dwFlags -
see INLINE\_FLAG\_xxx


dwReserved[4]
- Reserved for future use.


 


 **See Also :**


**[CDBEGINRECORD](CDBEGINRECORD.md)**


**[CDENDRECORD](CDENDRECORD.md)**


**[CDRESOURCE](CDRESOURCE.md)**


**[INLINE\_FLAG\_xxx](INLINE_FLAG_xxx.md)**


**[INLINE\_VERSION1](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA16C424215A6405852569830050C774)**



----------------------------------------------------------------------------------------------------------


 





