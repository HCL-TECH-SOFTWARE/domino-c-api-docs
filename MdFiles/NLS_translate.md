




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




**Initial Release 5.0**



**Function : Character Manipulation**



**NLS\_translate** **- Character
encoding translation routine.**


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**



NLS\_STATUS
LNPUBLIC **NLS\_translate(**  

      BYTE far \*pString,  

      WORD  Len,  

      BYTE far \*pStringTarget,  

      WORD far \*pSize,  

      WORD  ControlFlags,  

      NLS\_PINFO  pInfo**);**



**Description :**



NLS\_translate
translates the SOURCE input string and puts the resulting translation into the
TARGET output string.  ControlFlags control how the translation is performed
(e.g. LMBCS to UNICODE).  See the symbolic value NLS\_xxx (TRANSLATE) for a
complete list of control flags.


 


The Len
argument is either the actual byte-count length of the SOURCE input string or,
NLS\_NULLTERM.  NLS\_NULLTERM means that the input string IS NULL terminated and
thus, the string's length can be calculated via some flavor of strlen(). 
Otherwise the Len value is used as the SOURCE input string's actual length.


 


**Parameters :**



Input :  

pString  -  The SOURCE input string.  

  

Len  -  Length in bytes of input string. If the string is null terminated, you
may set this to NLS\_NULLTERM.  

  

pSize  -  Size in bytes of output buffer.  

  

ControlFlags  -  Flags to govern how translation is performed.  

  

pInfo  -  Pointer to a populated NLS\_INFO structure.  

  




Output :  

(routine)  -  NLS\_SUCCESS  

NLS\_BADPARM  

  

  

pStringTarget  -  Pointer to the TARGET output buffer containing resultant
data.  

  

pSize  -  The actual number of bytes written to the output buffer.  

  




 **See Also :**


**[NLS\_load\_charset](NLS_load_charset.md)**


**[NLS\_xxx (TRANSLATE)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/14462A7B807C17C08525662800466F4E)**



----------------------------------------------------------------------------------------------------------


 





