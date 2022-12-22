




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



**SECTokenFreeAttrList** **- Free an
attribute list**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



void
LNPUBLIC **SECTokenFreeAttrList(**  

      SSO\_LTPA2\_ATTR \*\*pAttrList,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Free an
attribute list associated with the LtpaToken2 type of token.  An LtpaToken2
token can have an attribute list included in the token to hold custom token
data.   Some routines that encounter LtpaToken2 type of SSO tokens can return
the list of attributes that have been found in LtpaToken2, for example an
attribute list may be returned by SECTokenValidate2() or SECTokenListValidate()
as part of detailed token information.  When SECTokenFreeAttrList() is called,
the list is freed, and the location of the attribute list is reset to be NULL.


 


**Parameters :**



Input :  

pAttrList  -  pointer to the location of the attribute list to free  

  

dwReserved  -  Must be 0, for future use  

  




Output :  

(routine)  -  None  

  

  

vpReserved  -  Must be NULL, for future use  

  




 **Sample Usage :**


STATUS error
= NOERROR;


SSO\_TOKEN\_INFO\_DESC
Info = {0};


SSO\_LTPA2\_ATTR
\*pMyAttrList = NULL;


 


/\*
Try to validate an LtpaToken2 token, e.g. a token found in an HTTP LtpaToken2
cookie. \*/


if
(error = SECTokenValidate2(


            NULL,


            pOrgName,


            pConfigName,   


            pTokenData,
/\* LtpaToken2 \*/


            SECTOKENFORMAT\_LTPATOKEN2,


            SECTOKEN\_RETURN\_USERNAME
| SECTOKEN\_RETURN\_ATTRIBUTE\_LIST,


            &Info,


            0,


            NULL


            ))


 
goto Done;


 


/\*
The validated token contains a user name that we asked to be returned in
Info.Username.ptr \*/


 


/\*
The validated token contains an LtpaToken2 attribute list that we asked to be
returned in Info.AttributesList  \*/


 


/\*
We're done with using the detailed token info, except we want to keep the
attribute list a little longer.  Free the username but keep the attribute list.
\*/


 


 pMyAttrList
= Info.AttributesList;


 


 SECTokenFreeInfo(
&Info, 


      
FALSE,


      
SECTOKEN\_RETURN\_USERNAME );


 


/\*
Now we're done with the attributes list, so free it. \*/


SECTokenFreeAttrList
(  &pMyAttrList, 0, NULL );    


 **See Also :**


**[SECTokenListGenerate](SECTokenListGenerate.md)**


**[SECTokenListValidate](SECTokenListValidate.md)**


**[SSO\_LTPA2\_ATTR](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9AFDD97FEC821B46482573FB003214E3)**



----------------------------------------------------------------------------------------------------------


 





