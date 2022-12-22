




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




**Initial Release 7.0**



**Data Type : Mail**



**SECGETSIGNERINFOPROC** **-** Callback
action routine for SECGetSignerInfoFromMail.


**----------------------------------------------------------------------------------------------------------**



**#include
<kfm.h>**



**Definition :**



typedef BOOL
(LNCALLBACKPTR SECGETSIGNERINFOPROC) (void  \*pCallCtx,


                                                
void  \*pCert,


                                                
DWORD CertSize,


                                         
        WORD  Reserved1,


                                                
WORD  Reserved2);


 


**Description :**



This is the
datatype of the action routine passed to SECGetSignerInfoFromMail.


     
pCallCtx             - (I) callers context passed intothe caller's callback
routine.  

     pCert                     - (I) pointer to an asn1encoded certificate  

     CertSize             - (I) size of certificate pointed to by pCert  

     Reserved1            - (I) reserved, should be ignored  

     Reserved2            - (I) reserved, should be ignored


 **See Also :**


**[SECGetSignerInfoFromMail](SECGetSignerInfoFromMail.md)**



----------------------------------------------------------------------------------------------------------


 





