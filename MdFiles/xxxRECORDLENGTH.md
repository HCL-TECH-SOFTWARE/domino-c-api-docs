




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




 


**Symbolic Value : Rich Text**



**xxxRECORDLENGTH** **-** Specifies
the number of bytes necessary to hold the length of a particular CD record.


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**


 **Symbolic Values :**      LONGRECORDLENGTH       -  The header is an LSIG structure
and the Length member is of type DWORD.  

  

      WORDRECORDLENGTH     -  The header is a WSIG structure and the Length
member is of type WORD.  

  

      BYTERECORDLENGTH       -  The header is a BSIG structure.  

  




**Description :**



Every CD
record begins with a header.  There are three types of headers, BSIG, WSIG, and
LSIG.  The first byte of the header is a signature which identifies the type of
the header and the type of the CD record that follows.   For the LSIG header,
the signature byte is OR'd with WORDRECORDLENGTH to produce a WORD signature. 
The Length member of the header is of type DWORD.  For the WSIG header, the
signature byte is OR'd with WORDRECORDLENGTH to produce a WORD signature.  The
Length member of the header is of type WORD.   For the BSIG header, the
signature is of type BYTE and the Length member of the header is also of type
BYTE.


 **See Also :**


**[BSIG](BSIG.md)**


**[LSIG](LSIG.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**


**[WSIG](WSIG.md)**



----------------------------------------------------------------------------------------------------------


 





