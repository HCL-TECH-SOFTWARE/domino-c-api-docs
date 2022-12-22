




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




**Initial Release 8.0.1**



**Data Type : Note**



**NOTE\_SEAL2\_HDR** **-** Seal header
infomation structure


**----------------------------------------------------------------------------------------------------------**



**#include
<addinout.h>**



**Definition :**



typedef
struct {


               DWORD
dwVersion;                            /\* Structure version number, currently
MBZ   \*/ 


                                    
        /\*   (must be zero)                          \*/


               DWORD
dwTotalRecordSize;            /\* Size of this record + variable data +     \*/


                                        
    /\*   extension descriptors and records       \*/


               DWORD
dwFlags;                                               /\* Flags, undefined bits
MBZ -               \*/


                                          
                /\*   see SEAL2HDR\_xxx below                  \*/


               DWORD
dwEntriesThisItem;             /\* Number of NOTE\_SEAL2s in this $Seal2 item \*/


               WORD 
wReserved;                     /\* Currently must be zero                    \*/


               WORD 
wBulkKeyLength;                 /\* Bulk key length                           \*/


               WORD 
wBulkKeyType;                     /\* Bulk key type                            
\*/


               WORD 
wAlgType;                                             /\* Bulk encryption
algorithm                 \*/


               DWORD
dwInitVectorLen;                  /\* Length of initialization vector, if any  
\*/


               DWORD
dwNumExtensions;                             /\* Number of header extension
records        \*/


                                                                            
/\* Variable header data follows:             \*/


                                                                            
/\*  BYTE initVector[dwInitVectorLen]         \*/


                                                                            
/\*  NOTE\_RECORD\_DESC recDesc[dwNumExtensions]\*/


                                                                            
/\*  dwNumExtensions extension records        \*/


}
NOTE\_SEAL2\_HDR;


 


**Description :**



Seal header
infomation structure.


 




----------------------------------------------------------------------------------------------------------


 





