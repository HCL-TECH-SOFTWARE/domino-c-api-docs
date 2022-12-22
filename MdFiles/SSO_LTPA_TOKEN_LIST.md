




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




**Initial Release 8.0**



**Data Type : SSO**



**SSO\_LTPA\_TOKEN\_LIST** **-** Structure to
store returned Ltpa tokens in a list.


**----------------------------------------------------------------------------------------------------------**



**#include
<bsafe.h>**



**Definition :**



typedef struct{                                                                /\*
Structure to store returned Ltpa tokens in a list.      \*/                                


        MEMHANDLE                                    mhSelf;                /\*
Memory allocated for this struct \*/


        SECTOKENFORMAT                        TokenType;


        MEMHANDLE                                    mhToken;


        SSO\_TOKEN                                    \*pToken;                     
/\* locked pointer to token allocated in mhToken \*/


        void                                         \*pNext;                /\*
struct SSO\_LTPA\_TOKEN\_LIST \* to next struct in list \*/


        }


        SSO\_LTPA\_TOKEN\_LIST;


 


 


**Description :**



Structure to
store returned Ltpa tokens in a list.


 




----------------------------------------------------------------------------------------------------------


 





