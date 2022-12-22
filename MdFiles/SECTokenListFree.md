




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




**Initial Release 8.0**



**Function : SSO**



**SECTokenListFree** **- Free all
SSO tokens in the list created by SECTokenListGenerate()**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



void
LNPUBLIC **SECTokenListFree(**  

      SSO\_LTPA\_TOKEN\_LIST \*\*pTokenList,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Free all SSO
tokens in the list created by SECTokenListGenerate().  The caller passes a
pointer to where the token list is located.  After freeing the token list, the
pointer to where the token list was located is reset to NULL.


 


**Parameters :**



Input :  

pTokenList  -  pointer to where the token list is located.  

  

dwReserved  -  Must be 0, for future use  

  




Output :  

(routine)  -  None  

  

  

vpReserved  -  must be NULL, for future use.  

  




 **Sample Usage :**


STATUS error
= NOERROR;


SSO\_LTPA\_TOKEN\_LIST
\*pTokenList = NULL;


 


if(
error = SECTokenListGenerate(         NULL,


            pOrgName,


            pConfigName,


            pUserName,


     
NULL, /\* default creation time \*/


     
NULL, /\* default expiration time \*/


     
NULL, /\* no attributes \*/


     
0, /\* no optional flags \*/


     
NULL, /\* no optional return info \*/


     
&pTokenList,


     
0, NULL))


            goto
Done;


 


SECTokenListFree(
&pTokenList, 0, NULL );


 **See Also :**


**[SECTokenListGenerate](SECTokenListGenerate.md)**


**[SSO\_LTPA\_TOKEN\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/39C994452C539B8E482573FB003214E2)**



----------------------------------------------------------------------------------------------------------


 





