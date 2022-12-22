




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




**Initial Release 7.0.2**



**Symbolic Value : MIME**



**MIME\_HEADER\_FORMAT\_xxx** **-** information
on how to map an Internet header to a Notes/Domino item.  

  




**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**


 **Symbolic Values :**      MIME\_HEADER\_FORMAT\_ADDRESS          -  header is an RFC822
address header.  

  

      MIME\_HEADER\_FORMAT\_DAT       -  header is an RFC822 date/time header.  

  

      MIME\_HEADER\_FORMAT\_NOTES\_ITEM    -  header is an X-Notes-Item header used
to preserve Notes/Domino items across SMTP transfers.  

  

      MIME\_HEADER\_FORMAT\_TEXT     -  header is text; map to TYPE\_TEXT.  

  

      MIME\_HEADER\_FORMAT\_TEXT\_LIST        -  header is a list; map to
TYPE\_TEXT\_LIST.  

  




**Description :**



information
on how to map an Internet header to a Notes/Domino item.


 


 




----------------------------------------------------------------------------------------------------------


 





