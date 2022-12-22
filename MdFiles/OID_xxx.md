




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : IDs**



**OID\_xxx** **-** ORIGINATORID
- Sequence


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      OID\_SEQNO\_MASK             -  Mask used to extract sequence.  

  

      OID\_NO\_REPLICATE           -  Never replicate outward, currently used
ONLY for deleted stubs.  

  




**Description :**



The Sequence
member of the ORIGINATORID structure is a DWORD used to keep track of the most
recent version of the note for replicated data purposes.  Sequence flags are
represented in the high order WORD of the Sequence member.  Use these symbols
to access the Sequence flags. 


 **See Also :**


**[ORIGINATORID](ORIGINATORID.md)**



----------------------------------------------------------------------------------------------------------


 





