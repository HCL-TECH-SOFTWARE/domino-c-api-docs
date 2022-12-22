




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



**SECTokenListGenerate** **- create
SSO tokens**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECTokenListGenerate(**  

      char \*ServerName,  

      char \*OrgName,  

      char \*ConfigName,  

      char \*UserName,  

      TIMEDATE \*Creation,  

      TIMEDATE \*Expiration,  

      void \*pAttributes,  

      DWORD  dwRequestedInfoFlags,  

      SSO\_TOKEN\_INFO\_DESC \*retpInfo,  

      SSO\_LTPA\_TOKEN\_LIST \*\*retpTokenList,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



For creating
one or more SSO tokens according to configuration.


 


The
inputs OrgName and ConfigName are used to locate the applicable configuration. 
The configuration determines which tokens are created and returned in
retpTokenList.  The supported tokens that currently could be returned in the
list include LtpaToken and LtpaToken2.  The caller takes responsibility to free
the token list by calling SECTokenListFree().


 


The
caller can request information about the preferred token (first) in the list. 
The output is to be returned in the caller's retpInfo struct.  Additional
output about the preferred token can be requested by setting the
dwRequestedInfoFlags so that the output is also returned in the retpInfo
struct.  


 


Currently
supported flags:


  
SECTOKEN\_RETURN\_RAWTOKENUSERNAME - return the user name exactly as it appears
in the token.


  
SECTOKEN\_RETURN\_RENEWAL\_TIME - return renewal information that may apply in
Domino-only configurations supporting idle session timeout.  A pointer to the
renewal timedate is returned in retpInfo->vpReservedTiming.


 


If
dwRequestedInfoFlags is non-zero, the caller must free the resources associated
with the output retpInfo by calling SECTokenFreeInfo().


 


**Parameters :**



Input :  

ServerName  -  Domino server to ask to generate the token list (reserved as
NULL).  

  

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if
not using 'Internet Sites' view for configuration)  

  

ConfigName  -  Name of Web SSO Configuration to use  

  

UserName  -  Canonicalized username to encode in the token.  This name could be
a Notes distinguished name, or a name in LDAP distinguished name format.  LDAP
format is more likely to be appropriate if name mapping is enabled (see
SECGetSSONameMappingConfig())   

  

Creation  -  Creation time to set for the token (specify NULL to use the
current time).  

  

Expiration  -  Expiration time to set for the token (specify NULL to use
expiration from specified Web SSO Configuration).  

  

pAttributes  -  currently ignored, for future use as input  

  

dwRequestedInfoFlags  -  SECTOKEN\_RETURN\_RAWTOKENUSERNAME:  

     For the preferred (i.e. first) token in the token list, return the format
of the name put in the token. If this flag is on, the
retpInfo->RawTokenUsername struct is populated.  

 SECTOKEN\_RETURN\_RENEWAL\_TIME:  

     For the preferred (i.e. first) token in the token list, return renewal
information that may apply in Domino-only configurations supporting idle
session timeout.  A pointer to the renewal timedate is returned in
retpInfo->vpReservedTiming.  

  

dwReserved  -  Must be 0  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully create the token list.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retpInfo  -  (optional) Return additional token information about the preferred
(i.e. first) token in the token list into the caller's SSO\_TOKEN\_INFO\_DESC
struct. To prepare for the receiving of information in the caller's struct, the
caller's struct should be initialized, storing zero in all fields. If retpInfo
is non-null, then the retpInfo on return will always contain the TokenType and
Expiration TIMEDATE information populated in the struct. The Creation TIMEDATE
is populated only if Domino-only configuration is in use. The caller can
request additional output information using the dwRequestedInfoFlags. If
dwRequestedInfoFlags is non-zero, the caller must free the resources associated
with the output retpInfo by calling SECTokenFreeInfo().    

  

retpTokenList  -  return pointer to the returned token list. The caller takes
responsibility to free the token list by calling SECTokenListFree().  

  

vpReserved  -  reserved for future use  

  




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


**[SECCreateTokenListEntry](SECCreateTokenListEntry.md)**


**[SECTokenListFree](SECTokenListFree.md)**


**[SSO\_LTPA\_TOKEN\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/39C994452C539B8E482573FB003214E2)**


**[SSO\_TOKEN](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/ABE1F48EEAFAA02E85256BC10067CE9E)**


**[SSO\_TOKEN\_INFO\_DESC](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/74730BCA8C6A2A2C482573FB003214E5)**



----------------------------------------------------------------------------------------------------------


 





