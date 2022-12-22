




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



**SECCreateTokenListEntry** **- Allocate
a new entry that can be inserted into a Single Sign-On  token list.**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECCreateTokenListEntry(**  

      SECTOKENFORMAT  TokenType,  

      char \*pToken,  

      char \*pTokenName,  

      char \*pDomainList,  

      WORD  wNumDomains,  

      BOOL  bSecureOnly,  

      SSO\_LTPA\_TOKEN\_LIST \*\*retpEntry,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Allocate a
new entry that can be inserted into a Single Sign-On  token list.  The entry
will usually just be storing a token that may need to be validated, therefore
it is optional to provide domain info settings etc associated with a browser
cookie.


 


**Parameters :**



Input :  

TokenType  -  one of SECTOKENFORMAT\_LTPATOKEN, SECTOKENFORMAT\_LTPATOKEN2,
SECTOKENFORMAT\_UNKNOWN  

  

pToken  -  a locked pointer to the token  

  

pTokenName  -  a locked pointer to the token name, e.g. cookie name such as "LtpaToken"
(can be NULL)  

  

pDomainList  -  locked pointer (always one domain only), or NULL  

  

wNumDomains  -  if non-zero, should currently always be 1  

  

bSecureOnly  -  currently always set to FALSE, for future use  

  

dwReserved  -  Must be 0, for future use.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retpEntry  -  location to store newly allocated entry.  Caller is responsible
to free using SECTokenListFree()  

  

vpReserved  -  should be NULL, for future use  

  




 **Sample Usage :**


STATUS error
= NOERROR;


SSO\_LTPA\_TOKEN\_LIST
\*pTokenEntry = NULL;


 


if
(error = SECCreateTokenListEntry( 


 
SECTOKENFORMAT\_LTPATOKEN, 


 
pLtpaData, /\* pointer to the LtpaToken found in HTTP cookie \*/ 


 
NULL, NULL, 0, FALSE, 


 
&pTokenEntry, 


 
0, NULL ))


 
goto Done;


 


/\*
Now do something with the returned pTokenEntry, e.g. validate it by calling
SECTokenListValidate()  \*/


 


 


/\*
Free when done with the entry \*/


SECTokenListFree
( &pTokenEntry, 0, NULL );


 **See Also :**


**[SECTOKENFORMAT](SECTOKENFORMAT.md)**


**[SECTokenListGenerate](SECTokenListGenerate.md)**


**[SECTokenListValidate](SECTokenListValidate.md)**


**[SSO\_LTPA\_TOKEN\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/39C994452C539B8E482573FB003214E2)**



----------------------------------------------------------------------------------------------------------


 





