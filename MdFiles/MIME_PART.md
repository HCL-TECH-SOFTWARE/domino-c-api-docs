




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



**Data Type : MIME**



**MIME\_PART** **-** Mime parts
record.


**----------------------------------------------------------------------------------------------------------**



**#include
<mimeods.h>**



**Definition :**



typedef struct {  

    WORD    wVersion;      /\* MIME\_PART Version \*/  

    DWORD   dwFlags;  

    BYTE    cPartType;     /\* Type of MIME\_PART body \*/  

    BYTE    cSpare;  

    WORD    wByteCount;    /\* Bytes of variable length part data  

                                  NOT including data in DB object\*/


 


    WORD    wBoundaryLen; 
/\* Length of the boundary string \*/  

    WORD    wHeadersLen;   /\* Length of the headers \*/  

    WORD    wSpare;  

    DWORD   dwSpare;


 


    /\*      Followed by
the actual part data \*/  

} MIME\_PART;


 


**Description :**



The
MIME\_PART structure stores the mime parts for items of TYPE\_MIME\_PART.  The
fields in this structure are:


 


wVersion                MIME\_PART
Version.


dwFlags                 Flags
- see MIME\_PART\_xxx.  

cPartType              Type of MIME\_PART body - see MIMEPARTTYPE.  

cSpare                   Spare BYTE.  

wByteCount                 Bytes of variable length part data NOT including
data in DB object.


wBoundaryLen        Length
of the boundary string.  

wHeadersLen          Length of the headers.  

wSpare                   Spare WORD.  

dwSpare                 Spare DWORD.


 


 **See Also :**


**[MIME\_PART\_VERSION](MIME_PART_VERSION.md)**


**[MIME\_PART\_xxx](MIME_PART_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





