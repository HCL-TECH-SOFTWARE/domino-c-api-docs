




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



**SECTokenValidate2** **- Validate
an SSO token**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECTokenValidate2(**  

      char \*ServerName,  

      char \*OrgName,  

      char \*ConfigName,  

      char \*TokenData,  

      SECTOKENFORMAT  AssumedType,  

      DWORD  dwRequestedInfoFlags,  

      SSO\_TOKEN\_INFO\_DESC \*retpInfo,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Validate an
SSO token.


 


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


 


**Parameters :**



Input :  

ServerName  -  Domino server to ask to validate the token. (Reserved as NULL)  

  

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if
not using 'Internet Sites' view for configuration)  

  

ConfigName  -  Name of Web SSO Configuration to use.  

  

TokenData  -  the SSO token to be validated (e.g. may be the value associated
with an HTTP cookie named "LtpaToken" or a cookie named "LtpaToken2")  

  

AssumedType  -  The caller gives information about what type of token is being
validated.  If the token has been received in an HTTP cookie, the AssumedType
of token would be evident to the caller based on the name of the cookie
(LtpaToken vs LtpaToken2). AssumedType can be set to SECTOKENFORMAT\_UNKNOWN,
however this may negatively impact performance.  If the routine does not know
the type of the token it is validating, it will try to validate the token as
any of the allowed token types in the configuration.  

  

dwRequestedInfoFlags  -  (optional) see detailed description  

  

dwReserved  -  Must be 0, for future use  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

    NOERROR - Successful.  

  

    ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  

retpInfo  -  (optional) Return additional token information about the validated
token in the token list into the caller's SSO\_TOKEN\_INFO\_DESC struct. To
prepare for the receiving of information in the caller's struct, the caller's
struct should be initialized, storing zero in all fields.  See detailed
description for options and information about freeing allocated resources.   

  

vpReserved  -  should be NULL, for future use    

  




 **Sample Usage :**


STATUS error
= NOERROR;


SSO\_TOKEN\_INFO\_DESC
Info = {0};


 


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


            SECTOKEN\_RETURN\_USERNAME,



            &Info,


            0,


            NULL


            ))


 
goto Done;


 


/\*
The validated token contains a user name that we asked to be returned in
Info.Username.ptr \*/


 


/\*
We're done with using the detailed token info so free it. \*/


SECTokenFreeInfo(
&Info, TRUE, 0 );


 **See Also :**


**[SECTOKENFORMAT](SECTOKENFORMAT.md)**


**[SECTokenListValidate](SECTokenListValidate.md)**


**[SECTokenValidate](SECTokenValidate.md)**


**[SSO\_TOKEN\_INFO\_DESC](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/74730BCA8C6A2A2C482573FB003214E5)**



----------------------------------------------------------------------------------------------------------


 





