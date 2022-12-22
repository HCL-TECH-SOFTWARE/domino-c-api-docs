




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDCTL** **-** Specifies an
embedded control window.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;         /\* Signature and length of this record. \*/  

   DWORD CtlStyle;   

   WORD  Flags;  

   WORD  Width;  

   WORD  Height;  

   WORD  Version;  

   WORD  CtlType;  

   WORD  MaxChars;  

   WORD  MaxLines;


   WORD  Percentage;


   DWORD Spare[3];


} CDEMBEDDEDCTL;


 


**Description :**



This CD
record may further define attributes within a CDFIELD such as tab order.


 


Header       


CtlStyle                  Embedded
control Style, see EC\_STYLE\_xxx


Flags                      Embedded
control Flags, see EC\_FLAG\_xxx


Width                     Width
of embedded control


Height                    Height
of embedded control


Version                   Embedded
control version, see EMBEDDEDCTL\_VERSIONxxx


CtlType                  Embedded
control type, see EBMEDDEDCTL\_xxx


MaxChars               Maximum
Characters


MaxLines                Maximum
Lines


Percentage


Spare[3]


 


 


 **See Also :**


**[EC\_DIALOGUNITS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D790B8E7E87556CA8525672E00773EE2)**


**[EC\_FITTOCONTENTS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2C6E6F95BF35FAF48525672E00782BE2)**


**[EC\_FLAG\_xxx](EC_FLAG_xxx.md)**


**[EC\_STYLE\_xxx](EC_STYLE_xxx.md)**


**[EMBEDDEDCTL\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/88D1F32A118DEBBD852566280041AD16)**


**[EMBEDDEDCTL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5368E0E80883A917852567310003ECAE)**



----------------------------------------------------------------------------------------------------------


 





