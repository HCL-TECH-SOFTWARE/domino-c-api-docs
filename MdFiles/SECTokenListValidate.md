




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



**SECTokenListValidate** **- Find the
preferred token in the list and validate it**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECTokenListValidate(**  

      char \*ServerName,  

      char \*OrgName,  

      char \*ConfigName,  

      SSO\_LTPA\_TOKEN\_LIST \*pTokenList,  

      SSO\_LTPA\_TOKEN\_LIST \*\*retpValidatedToken,  

      DWORD  dwRequestedInfoFlags,  

      SSO\_TOKEN\_INFO\_DESC \*retpInfo,  

      SSO\_LTPA\_TOKEN\_LIST \*\*retpCompatibilityToken,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Validate the
input Single Sign-On token list. The list can contain one or more tokens. This
routine will find the preferred token in the list and attempt to validate it.
If a token validation is not successful, the routine will investigate other
tokens in the list to find one which can be validated.  On success, a pointer
to the validated token is returned in retpValidatedToken. After a token in the
list is successfully validated, the rest of the list may be ignored. 


 


The
routine can return detailed information about the token which has been
validated.  The info returned will be the info from the token pointed to by the
returned retpValidatedToken, which is, according to the configuration, the
preferred token in the list.  If the caller wants to validate each token
individually, the caller should use SECTokenValidate2 instead for each token
(because this routine only returns results for the preferred token in the
list).


 


The
caller can request information about the validated token to be returned in
retpInfo struct. If retpInfo is non-null, then the retpInfo will always contain
this output:


  
TokenType -- currently either SECTOKENFORMAT\_LTPATOKEN or
SECTOKENFORMAT\_LTPATOKEN2


  
Expiration


  
Creation (if Domino format token)


Optional
output is requested by setting the dwRequestedInfoFlags.  Currently supported
flags:


 
SECTOKEN\_RETURN\_USERNAME - return the name of the user whom this token
represents.


 
SECTOKEN\_RETURN\_RAWTOKENUSERNAME - return the user name exactly as it appears
in the token.


 
SECTOKEN\_RETURN\_ATTRIBUTE\_LIST - return the attribute list contained in an
LtpaToken2 token.


 
SECTOKEN\_RETURN\_RENEWAL\_TIME - return renewal information that may apply in
Domino-only configurations supporting idle session timeout.  A pointer to the
renewal timedate is returned in retpInfo->vpReservedTiming. 


 


If
dwRequestedInfoFlags is non-zero, the caller must free the resources associated
with the output retpInfo by calling SECTokenFreeInfo().


 


For
WebSphere-compatible SSO configurations, the SSO configuration may specify the
use of both LtpaToken and LtpaToken2 (sometimes referred to as compatibility
mode).  This routine can check for the existence of both of these tokens.  If
one token type is in the token list, but the other token type is not in the
list, the caller can request the routine to create the missing token type (i.e.
the compatibility token). The caller can request a compatibility token in
retpCompatibilityToken, which would be returned only if the configuration is in
compatibility mode and if the pTokenList does not already contain both
LtpaToken and LtpaToken2. If a compatibility token is returned, it must be
freed by the caller using SECTokenListFree().


 


**Parameters :**



Input :  

ServerName  -  Domino server to ask to validate the token. (Reserved as NULL)  

  

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if
not using 'Internet Sites' view for configuration)  

  

ConfigName  -  Name of Web SSO Configuration to use.  

  

pTokenList  -  the list of tokens on which validation should be attempted.  For
example, LtpaToken may be detected in the HTTP stream.  LtpaToken can be
converted into an entry in a token list by calling SECCreateTokenListEntry().  

  

dwRequestedInfoFlags  -  (optional)see long description for information about
the flags  

  

dwReserved  -  Must be 0, for future use  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - success  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retpValidatedToken  -  pointer to which of the tokens in the list has been
successfully validated. Note that info for this token entry in the list may be
updated during the course of this call if the token entry was previously of
unknown type (tokenType updated), or if SSO\_TOKEN info (name, domainlist,
domainnum) was unspecified in the caller's list entry.  

  

retpInfo  -  (optional) Return additional token information about the validated
token in the token list into the caller's SSO\_TOKEN\_INFO\_DESC struct. To
prepare for the receiving of information in the caller's struct, the caller's
struct should be initialized, storing zero in all fields.  See detailed
description for options and information about freeing allocated resources.   

  

retpCompatibilityToken  -  (optional).  Location to return a compatibility
token, which must be freed by the caller using SECTokenListFree(). see long
description for compatibility token information  

  

vpReserved  -  must be NULL, for future use  

  




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


            NULL,
/\* no compatibility token needed \*/


            0,
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


**[SECCreateTokenListEntry](SECCreateTokenListEntry.md)**


**[SECTokenValidate](SECTokenValidate.md)**


**[SECTokenValidate2](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/C16D33DBDE9CAB59482573FB00322847)**


**[SSO\_LTPA\_TOKEN\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/39C994452C539B8E482573FB003214E2)**


**[SSO\_TOKEN\_INFO\_DESC](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/74730BCA8C6A2A2C482573FB003214E5)**



----------------------------------------------------------------------------------------------------------


 





