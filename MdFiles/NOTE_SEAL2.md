




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




**Initial Release 8.0.1**



**Data Type : Note**



**NOTE\_SEAL2** **-** Note seal
structure


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {


        DWORD
dwVersion;                      /\* Structure version number, currently MBZ   \*/


        DWORD
dwTotalRecordSize;              /\* Size of this record + variable data +     \*/


                                   
          /\*   extension descriptors and records       \*/


        DWORD
dwFlags;                        /\* Flags, undefined bits MBZ. Defined below  \*/


        WORD 
wKEKType;                              /\* Key encryption key type 
(SEC\_ki\_xxx)     \*/


        WORD 
wAlgType;                              /\* Encryption algorithm used to encrypt
the  \*/


                                   
          /\*   bulk (data) encryption key (SEC\_ai\_xxx) \*/


        TIMEDATE
tdSealed;                    /\* When the seal was created                 \*/


        DWORD
dwEncryptedBulkKeyLength;       /\* Length of the encrypted bulk data key \*/


        DWORD
dwNumExtensions;                /\* Number of extension records               \*/


                                             /\* 
Variable data follows:                                                   \*/


                                             /\*
 BYTE              encryptedBulkKey[dwEncryptedBulkKeyLength]             \*/


                                             /\* 
NOTE\_RECORD\_DESC  recDesc[dwNumExtensions]                               \*/


                                             /\* 
dwNumExtensions extension records of various types                       \*/


} NOTE\_SEAL2;


 


**Description :**



Note seal
structure.


 




----------------------------------------------------------------------------------------------------------


 





