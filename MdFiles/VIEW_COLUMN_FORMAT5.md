




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




**Initial Release 6.5**



**Data Type : Views**



**VIEW\_COLUMN\_FORMAT5** **-** Extended
View column format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct


        {


        WORD    Signature;                    /\*
VIEW\_COLUMN\_FORMAT\_SIGNATURE5 \*/


        WORD    dwLength;                     /\*
sizeof this structure + any extra data. \*/


        /\*
Names style formatting data. \*/


        DWORD   dwFlags;               


        WORD    wDistNameColLen;              /\*
Length of programatic name of column that contains distiguished name. \*/


        WORD    wSharedColumnAliasLen; /\*
If shared column, length of the alias of the shared column \*/


        DWORD   dwReserved[4];         /\*
Reserved for future use. \*/


        }
VIEW\_COLUMN\_FORMAT5;


 


 **See Also :**


**[VCF5\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/36E311BE4AFF68B185256D5600681B43)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_COLUMN\_FORMAT\_SIGNATURE5](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70F031AE60C7BC8285256D5600677837)**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**



----------------------------------------------------------------------------------------------------------


 





