




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



**Function : Basic Encoding Rules;
LDAP**



**ber\_free** **- Frees a
BerElement.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



void
LNPUBLIC **ber\_free(**  

      BerElement \*ber,  

      int  freebuf**);**



**Description :**



Frees a
BerElement which is returned from the API calls ber\_alloc\_t() or ber\_init(). 
Each BerElement should be freed by the caller.


 


Implemented
as a macro:


 


#define
ber\_free(ber, freebuf)                      ND\_ber\_free((ber), (freebuf))


 


**Parameters :**



Input :  

ber  -  Pointer to a BerElement structure.  

  

freebuf  -  BER functions always set this parameter to 1 to ensure that the
internal buffer used by the BER functions is freed as well as the BerElement
container itself. (Note: LDAP functions set this parameter to 0).  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**



ber\_free(ber,
0);


 


 **See Also :**


**[BerElement](BerElement.md)**


**[ber\_alloc\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3CBFE85E4F1A206785256F5C00486F0D)**


**[ber\_init](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/191D4002B669A6FB85256F5C00486F0E)**



----------------------------------------------------------------------------------------------------------


 





