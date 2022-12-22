




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



**Data Type : User Registration**



**SSO\_TOKEN** **-** Structure
that defines a Single Sign-On token.


**----------------------------------------------------------------------------------------------------------**



**#include
<bsafe.h>**



**Definition :**



typedef struct{


      MEMHANDLE   mhName;


      MEMHANDLE   mhDomainList;


      WORD        wNumDomains;


      BOOL        bSecureOnly;


      MEMHANDLE   mhData;


    }
SSO\_TOKEN;


 


**Description :**



This
structure contains information representing an authentication token used for
Single Sign-On. The typical use is to store this information in a browser
'cookie' for interoperability with Domino protocols that support Single Sign-On
(IE: HTTP and DIIOP), as well as IBM WebSphere Advanced Server.


 


mhName          -
MEMHANDLE to a null-terminated name for the token when set as a cookie. Access
with OSMemoryLock.


mhDomainList   -
MEMHANDLE to a list of null-delimited DNS domains for the token when set as a
cookie. Access with OSMemoryLock.


wNumDomains -
Total number of domains contained in the mhDomainList member.


bSecureOnly     -
BOOL recommending that the token only be set on a secure connection.


mhData            -
MEMHANDLE to a the null-terminated token data.


 


See the
Domino Administrators Guide for information on configuring Single Sign-On.


 


 **See Also :**


**[SECTokenFree](SECTokenFree.md)**


**[SECTokenGenerate](SECTokenGenerate.md)**


**[SECTokenValidate](SECTokenValidate.md)**



----------------------------------------------------------------------------------------------------------


 





