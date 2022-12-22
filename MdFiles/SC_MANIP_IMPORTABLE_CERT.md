




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




**Initial Release 6.0.2**



**Data Type : Smartcards**



**SC\_MANIP\_IMPORTABLE\_CERT** **-** Structure
used for SC\_manip\_GetMatchedCert


**----------------------------------------------------------------------------------------------------------**



**#include
<kfm.h>**



**Definition :**



typedef struct


{


        DWORD
Version;     /\* This typedef describes version 0 \*/


        DWORD
dwSize; 


        DWORD
dwUnused;


        DWORD
retIDLen;


        DWORD
retLabelLen;


        DWORD
retCertLen;


        DWORD
IDOffset;    /\* Offset in bytes from beginning of structure \*/


        DWORD
LabelOffset; /\* Offset in bytes from beginning of structure \*/


        DWORD
CertOffset;  /\* Offset in bytes from beginning of structure \*/


        /\*
ID \*/


        /\*
Label \*/


        /\*
Cert \*/


}


SC\_MANIP\_IMPORTABLE\_CERT;


 


**Description :**



SC\_MANIP\_IMPORTABLE\_CERT
is used with the SECManipulateSC OpCode SC\_manip\_GetMatchedCert (in
SC\_manip\_xxx) to examine the certificates that are available for import from
the Smartcard into the ID file.  

  




Version -
Must be 0 for this version of the structure.


 


dwSize -The
size of the memory block including this structure.


 


dwUnused -
Unused.


 


retIDLen -
The ID length.


 


retLabelLen
- The label length.


 


retCertLength
- The certificate length.  

  




IDOffset  -
The key identifier, common to the X.509 certificate and the associated private
key.  

  




LabelOffset
- The certificate's label, defined by the PKCS #11 specification as a string
"intended to assist users in browsing".   

  




CertOffset
-  The X.509 certificate.


 **See Also :**


**[SC\_manip\_xxx](SC_manip_xxx.md)**


**[SECManipulateSC](SECManipulateSC.md)**



----------------------------------------------------------------------------------------------------------


 





