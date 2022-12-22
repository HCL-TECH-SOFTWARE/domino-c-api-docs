




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




 


**Data Type : Time**



**TFMT** **-** Formats for
character time/date string conversions.


**----------------------------------------------------------------------------------------------------------**



**#include
<misc.h>**



**Definition :**



typedef struct {  

   BYTE Date;  /\* Date Display Format \*/  

   BYTE Time;  /\* Time Display Format \*/  

   BYTE Zone;      /\* Time Zone Display Format    \*/  

   BYTE Structure; /\* Overall Date/Time Structure \*/  

} TFMT;  

  




 


**Description :**



This
structure holds the format for character time/date strings. You set up this
structure based on the time/date format you want to use. Definitions for the
various fields of this structure are found in TDFMT\_xxx, TTFMT\_xxx, TZFMT\_xxx,
and TSFMT\_xxx.


 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[TDFMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/001F0025000A002585255EAA00705CC5)**


**[TSFMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BC4E4F5E3FEE9E128525621B00408BD4)**


**[TTFMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8D7EC5047D79E4658525621B003F6F5A)**


**[TZFMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/659769E36672989A8525621B00408849)**



----------------------------------------------------------------------------------------------------------


 





