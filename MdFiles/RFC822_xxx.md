




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




**Initial Release 5.0.7**



**Symbolic Value : RFC822**



**RFC822\_xxx** **-** RFC822ITEMDESC
- dwFlags


**----------------------------------------------------------------------------------------------------------**



**#include <mimeods.h>**


 **Symbolic Values :**      RFC822\_ITEM\_FORMAT\_MASK       -  Format mask.  

  

      RFC822\_ITEM\_FORMAT\_ADDR       -  822-header is an address.  

  

      RFC822\_ITEM\_FORMAT\_DATE       -  822-header is a date.  

  

      RFC822\_ITEM\_FORMAT\_TEXT       -  822-header is text.  

  

      RFC822\_ITEM\_STORAGE\_STRICT             -  STRICT storage format.  

  

      RFC822\_ITEM\_TEXT\_LIST   -  Text item is TEXT\_LIST.  

  

      RFC822\_TEXT\_UNUSED     -  First available flag.  

  




**Description :**



Possible
TYPE\_822\_TEXT values for the dwFlags member of the RFC822ITEMDESC structure. 
The first three bits are reserved for the RFC822\_ITEM\_FORMAT\_MASK format mask, 
the formats defined include: RFC822\_ITEM\_FORMAT\_ADDR, RFC822\_ITEM\_FORMAT\_DATE
and RFC822\_ITEM\_FORMAT\_TEXT.  The remaining bits are flags which include:
RFC822\_ITEM\_STORAGE\_STRICT, RFC822\_ITEM\_TEXT\_LIST and RFC822\_TEXT\_UNUSED.


 **See Also :**


**[RFC822ITEMDESC](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A4C56487FB6A338185256A2500415BAF)**



----------------------------------------------------------------------------------------------------------


 





