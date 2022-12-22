




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



**SETDATABORDERTYPE** **- Set the
data border type bits stored in a Flags member of the CDDATAFLAGS structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



DWORD **SETDATABORDERTYPE(**  

      DWORD  a,  

      DWORD  b**);**



**Description :**



This macro
sets the data border type bits of a Flags member of the CDDATAFLAGS structure
and is defined as follows:


 


#define
SETDATABORDERTYPE(a,b) a = ((DWORD)((a) & ~BARREC\_DATA\_BORDER\_MASK) | 


                                  
((DWORD)(b - BAR\_DATA\_BORDER\_OFFSET)))


 


**Parameters :**



Input :  

a  -  A Flags member of the CDDATAFLAGS structure that is to have the data
border type set.  

  

b  -  The data border type value.  See the BARREC\_DATA\_BORDER\_xxx symbolic for
possible values.  

  




Output :  

(routine)  -  Flags member of the CDDATAFLAGS structure with the data border
type set.  

  

  

a  -  The Flags member of the CDDATAFLAGS structure that has the data border
type set to the value specified in the b parameter.  

  




 **See Also :**


**[BARREC\_DATA\_BORDER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/90ADB3E4E2033454852569D700621122)**


**[CDDATAFLAGS](CDDATAFLAGS.md)**



----------------------------------------------------------------------------------------------------------


 





