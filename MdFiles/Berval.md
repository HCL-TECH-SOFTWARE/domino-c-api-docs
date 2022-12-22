




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



**Data Type : Basic Encoding Rules;
LDAP**



**Berval** **-** Structure
for returning a sequence of octet strings + length


**----------------------------------------------------------------------------------------------------------**



**#include
<lber.h>**



**Definition :**



typedef struct berval {


        ber\_len\_t              bv\_len;


        char                   \*bv\_val;


}  Berval;


 


**Description :**



A Berval
structure represents binary data that is encoded using simplified Basic
Encoding Rules (BER). The data and size of the data are included in a Berval
structure as it contains a sequence of bytes and an indication of its length. 
Applications may allocate their own Berval structures.


 


The fields
in this structure are:


 


bv\_len           
The length of the data in bytes. This member must always be a nonnegative
number.


bv\_val           
The pointer to the binary data. This member is not null terminated.


 


The
Berval structure should be disposed of using ber\_bvfree().


 **See Also :**


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**



----------------------------------------------------------------------------------------------------------


 





