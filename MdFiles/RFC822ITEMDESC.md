




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




**Initial Release 5.0.7**



**Data Type : RFC822**



**RFC822ITEMDESC** **-** TYPE\_822\_TEXT
item RFC822 header information.


**----------------------------------------------------------------------------------------------------------**



**#include
<mimeods.h>**



**Definition :**



typedef struct {  

    WORD    wVersion;              /\* ODSSizeof this structure for versioning
\*/  

    DWORD   dwFlags;               /\* TYPE\_822\_TEXT flags.  The first three
bits  

                                     are reserved for the format mask,the
remaining bits are flags \*/  

    WORD    wNotesNativeLen;       /\* Length of the Notes version which is
either  

                                     a LMBCS string or a TIMEDATE. \*/  

    WORD    w822NameLen;   /\* Length of the original 822 header name \*/  

    WORD    w822DelimLen;  /\* Length of the original 822 header delimiter \*/


    WORD    w822BodyLen;   /\*
Length of the original 822 header body in  

                                     it's native charset and encoding (RFC2047)
\*/  

} RFC822ITEMDESC;


 


**Description :**



The
RFC822ITEMDESC structure stores the message header for items of
TYPE\_RFC822\_TEXT.  The fields in this structure are:


 


wVersion                ODSSizeof
this structure for versioning.  

dwFlags                 TYPE\_822\_TEXT flags.  The first three bits are reserved
for the format mask, the remaining bits are flags (See RFC822\_xxx).   

wNotesNativeLen    Length of the Notes version which is either a LMBCS string
or a TIMEDATE.  

w822NameLen        Length of the original 822 header name.  

w822DelimLen        Length of the original 822 header delimiter.


w822BodyLen         Length
of the original 822 header body in it's native charset and encoding (RFC2047).


 


 **See Also :**


**[RFC822\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F3394A4E5437993B85256A2500415BB0)**



----------------------------------------------------------------------------------------------------------


 





