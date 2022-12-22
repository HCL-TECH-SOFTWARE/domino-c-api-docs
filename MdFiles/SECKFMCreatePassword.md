




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : User Registration**



**SECKFMCreatePassword** **- Returns
the encoded password, given a non-encoded password.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



VOID
LNPUBLIC **SECKFMCreatePassword(**  

      char far \*pPassword,  

      KFM\_PASSWORD far \*retHashedPassword**);**



**Description :**



This
function returns the encoded password, given a non-encoded password.


 


**Parameters :**



Input :  

pPassword  -  Non-encoded password.  

  




Output :  

(routine)  -  None  

  

  

retHashedPassword  -  Pointer to the returned encoded password.  This is used
in SECKFMGetCertifierCtx to obtain a certifier context.  

  




 **See Also :**


**[NSFDB2DeleteUsernamePW](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E4450D50AF2A320385256EBD0047CC10)**


**[NSFDB2GetUsernamePW](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EECEF8A84ECDF6C185256EBD00447C5A)**


**[NSFDB2PutUsernamePW](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/773144A75529617585256EBD0046A1A5)**


**[SECKFMGetCertifierCtx](SECKFMGetCertifierCtx.md)**



----------------------------------------------------------------------------------------------------------


 





