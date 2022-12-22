




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




**Initial Release 6**



**Data Type : Views**



**VIEW\_COLUMN\_FORMAT4** **-** Extended
View column format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct  

{  

   WORD  Signature;          /\* VIEW\_COLUMN\_FORMAT\_SIGNATURE4 \*/  

                             /\* Numeric symbol data \*/  

   NFMT  NumberFormat;  

   BYTE  NumSymPref;         /\* NPREF\_xxx \*/  

   BYTE  NumSymFlags;        /\* NNUMSYM\_xxx \*/  

   DWORD DecimalSymLength;  

   DWORD MilliSepSymLength;  

   DWORD NegativeSymLength;  

   WORD  MilliGroupSize;  

   DWORD Unused1;  

   DWORD Unused2;  

                             /\* Currency data \*/  

   BYTE  CurrencyPref;       /\* NPREF\_xxx \*/  

   BYTE  CurrencyType;       /\* NCURFMT\_xxx \*/  

   BYTE  CurrencyFlags;      /\* NCURFMT\_xxx \*/  

   DWORD CurrencySymLength;  

   DWORD ISOCountry;  

   WORD  NumberPreference;   

   BYTE  bUnused;  

   DWORD Unused3;  

   DWORD Unused4;  

} VIEW\_COLUMN\_FORMAT4;


 


 **See Also :**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**



----------------------------------------------------------------------------------------------------------


 





