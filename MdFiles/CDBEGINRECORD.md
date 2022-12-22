




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



**CDBEGINRECORD** **-** Defines the
beginning of a CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG Header;    /\* Signature and length of this record \*/  

   WORD Version;            

   WORD Signature; /\* Signature of record begin is for \*/


} CDBEGINRECORD;


 


**Description :**



This CD
record defines the beginning of a series of CD Records.  Not all CD records are
enclosed within a CDBEGINRECORD/CDENDRECORD combination.  For those CD records
that are enclosed within a CDBEGINRECORD/CDENDRECORD combination, the Version
element is defined in the following table.


 


 





|  |  |  |
| --- | --- | --- |
| **CD Signature** | **Version Value** | **Symbol (if any)** |
| SIG\_CD\_BAR | 0 | BAR\_VERSION1 |
| SIG\_CD\_OLEBEGIN | 0 |   |
| SIG\_CD\_FIELD | 0 |   |
| SIG\_CD\_EMBEDDEDCTL | 0 | EMBEDDEDCTL\_VERSION1 |
| SIG\_CD\_GRAPHIC | 1 | CDGRAPHIC\_VERSION2 |
| SIG\_CD\_V4HOTSPOTBEGIN | 0 |   |
| SIG\_CD\_HORIZONTALRULE | 1 | CDHORIZONTALRULE\_VERSION1 |
| SIG\_CD\_KEYWORD | 0 |   |
| SIG\_CD\_LINK2 | 0 | LINK\_VERSION1 |
| SIG\_CD\_MAPELEMENT | 1 | CDMAPELEMENT\_VERSION1 |
| SIG\_CD\_AREAELEMENT | 1 | CDAREAELEMENT\_VERSION1 |
| SIG\_CD\_TEXT | 0 |   |
| SIG\_CD\_PRETABLEBEGIN | 1 |   |
| SIG\_CD\_BUTTON | 0 | BUTTON\_VERSION1 |
| SIG\_CD\_LAYER | 2 | CDLAYER\_VERSION2 |



 


Header       Defines
the record as a CDBEGINRECORD.


Version       Version
of this element.  (Note see table above)


Signature    Defines
the CD Signature the CDBEGINRECORD is for.


 


 


 **See Also :**


**[BAR\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/072A1D7A312DB99685256678004A471F)**


**[BUTTON\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/255BCDC39E05408485256A68004CBDDE)**


**[CDAREAELEMENT\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1D58C473E2DDA6B485256678004D4DA2)**


**[CDBUTTON](CDBUTTON.md)**


**[CDENDRECORD](CDENDRECORD.md)**


**[CDGRAPHIC\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E123A1E654110C13852562030071B820)**


**[CDHORIZONTALRULE\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/510A4C5E81862CF385256678004A6B7A)**


**[CDMAPELEMENT\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7ED455B0B35B74E785256678004D389E)**


**[EMBEDDEDCTL\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/88D1F32A118DEBBD852566280041AD16)**


**[LINK\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/621D9F136AB5119A852566780048ABEC)**



----------------------------------------------------------------------------------------------------------


 





