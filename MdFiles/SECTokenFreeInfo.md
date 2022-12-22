




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



**SECTokenFreeInfo** **- Free
information returned about a specific SSO token by SECTokenListGenerate(),
SECTokenListValidate(), SECTokenValidate2()**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



void
LNPUBLIC **SECTokenFreeInfo(**  

      SSO\_TOKEN\_INFO\_DESC \*pInfo,  

      BOOL  bFreeAll,  

      DWORD  dwRequestedInfoFlags**);**



**Description :**



Free
information returned about a specific SSO token by SECTokenListGenerate(),
SECTokenListValidate(), SECTokenValidate2().  The respective token routine may
have dynamically allocated memory in order to return detailed information about
a token, and the SECTokenFreeInfo() routine ensures that this associated memory
is freed.  The caller's input struct may contain a variety of items.  If the
caller wishes to specify which items should be freed and which should not be
freed (perhaps some items the caller has longterm use for and will free later),
the caller can pass in flags to declare which items should be freed. After
memory has been freed, the pointers in the caller's struct may become
re-initialized to NULL.


 


**Parameters :**



Input :  

pInfo  -  A pointer to the caller's struct that was passed to a token routine
for returning more detailed information about a token.  

  

bFreeAll  -  If TRUE, then free all allocated items in the pInfo struct.  

  

dwRequestedInfoFlags  -  If bFreeAll is FALSE, then only free those items
associated with flags passed in.  Flags may be SECTOKEN\_RETURN\_USERNAME  

SECTOKEN\_RETURN\_RAWTOKENUSERNAME  

SECTOKEN\_RETURN\_ATTRIBUTE\_LIST  

SECTOKEN\_RETURN\_RENEWAL\_TIME  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**


STATUS error
= NOERROR;


SSO\_LTPA\_TOKEN\_LIST        \*pValidatedToken
= NULL;


SSO\_TOKEN\_INFO\_DESC
Info = {0};


 


if
(error = SECTokenListValidate(           NULL,


     
pOrgName,


            pCfgName,


            pTokenList,


            &pValidatedToken,


            SECTOKEN\_RETURN\_USERNAME,



            &Info,


            NULL,   0,
NULL))


            goto
Done;


 


/\*
The token in the token list that was successfully validated is now pointed to
by pValidatedToken. \*/


 


/\*
The validated token contains a user name that we asked to be returned in
Info.Username.ptr \*/


 


/\*
We're done with using the detailed token info so free it. \*/


SECTokenFreeInfo(
&Info, TRUE, 0 );


 **See Also :**


**[SECTokenListGenerate](SECTokenListGenerate.md)**


**[SECTokenListValidate](SECTokenListValidate.md)**


**[SECTokenValidate2](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/C16D33DBDE9CAB59482573FB00322847)**


**[SSO\_TOKEN\_INFO\_DESC](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/74730BCA8C6A2A2C482573FB003214E5)**


**[SSO\_TOKEN\_ITEM](SSO_TOKEN_ITEM.md)**



----------------------------------------------------------------------------------------------------------


 





