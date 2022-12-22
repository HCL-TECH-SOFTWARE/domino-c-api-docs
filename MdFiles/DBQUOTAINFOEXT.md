




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



**Data Type : Database**



**DBQUOTAINFOEXT** **-** Extended
database quota structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**




typedef
struct {


   DWORD
WarningThreshold;    /\* Database size warning threshold in kbyte units \*/


   DWORD
SizeLimit;           /\* Database size limit in kbyte units \*/


   DWORD
CurrentDbSize;       /\* Current size of database (in kbyte units) \*/


   DWORD
MaxDbSize;           /\* Max database file size possible (in kbyte units) \*/


   WORD
QuotaMethod;          /\* Enforcement method - filesize or usage \*/


   DWORD
CurrentUsage; /\* Current amount of space used in the database (in kbyte units)
\*/


   DWORD
CurrentSizeUsed;     /\* Either CurrentDbSize, or CurrentUsage, depending on
method in use \*/


   DWORD
Unused1;             /\* Reserved.  Unused \*/


   DWORD
Unused2;             /\* Reserved.  Unused \*/


}
DBQUOTAINFOEXT;


 


**Description :**



This
structure is returned by NSFDbQuotaGethDB().  It contains the database quota
information and quota method.


 **See Also :**


**[DBQUOTAINFO](DBQUOTAINFO.md)**


**[NSF\_QUOTA\_METHOD\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/84D1198A00D468DC85256B27006A7861)**



----------------------------------------------------------------------------------------------------------


 





