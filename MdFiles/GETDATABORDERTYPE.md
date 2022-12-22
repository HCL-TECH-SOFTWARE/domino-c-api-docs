




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



**Function : Rich Text**



**GETDATABORDERTYPE** **- Return
the data border type value stored in a CDDATAFLAGS structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



DWORD **GETDATABORDERTYPE(**  

      DWORD  a**);**



**Description :**



This macro
returns the data border type value that is stored in the CDDATAFLAGS structure
and is defined as follows:


 


#define
GETDATABORDERTYPE(a) (((DWORD)((a) & BARREC\_DATA\_BORDER\_MASK )) +
BAR\_DATA\_BORDER\_OFFSET)


 


See the
BARREC\_DATA\_BORDER\_xxx symbolic for possible return values.


 


**Parameters :**



Input :  

a  -  A Flags member of the CDDATAFLAGS structure.  This macro returns the
border type that is stored in this DWORD.  

  




Output :  

(routine)  -  The border type that is set in the Flags member of a CDDATAFLAGS
structure.  See the BARREC\_DATA\_BORDER\_xxx symbolic values.  

  

  




 **See Also :**


**[BARREC\_DATA\_BORDER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/90ADB3E4E2033454852569D700621122)**


**[CDDATAFLAGS](CDDATAFLAGS.md)**



----------------------------------------------------------------------------------------------------------


 





