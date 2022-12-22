




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




**Initial Release 6**



**Function : LDAP**



**ldap\_parse\_result** **- Check for
an error of an asynchronous function.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_parse\_result(**  

      LDAP \*ld,  

      LDAPMessage \*result,  

      int \*errorcodep,  

      char \*\*matcheddnp,  

      char \*\*errmsgp,  

      char \*\*\*referralsp,  

      LDAPControl \*\*\*serverctrlsp,  

      int  freeit**);**



**Description :**



This
function will extract information from results and handle errors returned by
other LDAP API routines.  


 


Note that
ldap\_parse\_sasl\_bind\_result() and ldap\_parse\_extended\_result must typically be
used in addition to ldap\_parse\_result to retrieve all the result information
from SASL Bind and Extended Operations respectively.  The ldap\_parse\_result,
ldap\_parse\_sasl\_bind\_result, and  

ldap\_parse\_extended\_result functions all skip over messages of type
LDAP\_RES\_SEARCH\_ENTRY and LDAP\_RES\_SEARCH\_REFERENCE when looking for a result
message to parse.  See LDAP\_RES\_xxx.  If a chain of messages that contains more
than one result message is passed to these routines they always operate on the
first result in the chain.


 


Implemented
as a macro:


 


#define
ldap\_parse\_result(ld, result, errcodep, matcheddnp, errmsgp, referralsp,
serverctrlsp, freeit) \


             
ND\_ldap\_parse\_result((ld), (result), (errcodep), (matcheddnp), (errmsgp),
(referralsp), (serverctrlsp), (freeit))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

result  -  The result of an LDAP operation as returned by ldap\_result or one of
the synchronous API operation calls.  

  

errorcodep  -  NULL, to ignore this field.  

  

matcheddnp  -  NULL, to ignore this field.  

  

errmsgp  -   NULL, to ignore this field.  

  

referralsp  -  NULL, to ignore this field.  

  

serverctrlsp  -  NULL, to ignore this field.  

  

freeit  -  A boolean that determines whether the result parameter is  disposed
of or not.  If freeit is non-zero, the entire chain of messages represented by
result is disposed of after extracting the requested information. This is
provided as a convenience; zero can also be passed, to not free the messages,
and ldap\_msgfree can be used to free the result later.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

errorcodep  -  The LDAP  resultCode field from the LDAPMessage message.  This
is the indication from the server of the outcome of the operation.  

  

matcheddnp  -  If the server returned a matchedDN string to indicate how much
of a name passed in a request was recognized, this result parameter will be
filled in with that matchedDN string.  The matched DN string SHOULD be freed by
calling ldap\_memfree.  Note that the server may return a zero length matchedDN
(in which case \*matchednp is set to an allocated copy of "") which is
different than not returning a value at all (in which case \*matcheddnp is set
to NULL).  

  

errmsgp  -  This result parameter will be filled in with the contents of the
error message field from the LDAPMessage message.  The error message string
SHOULD be freed by calling ldap\_memfree.   

  

referralsp  -  This result parameter will be filled in with the contents of the
referrals field from the LDAPMessage message, indicating zero or more alternate
LDAP servers where the request is to be retried.  The referrals array SHOULD be
freed by calling ldap\_value\_free.   If no referrals were returned, \*referralsp
is set to NULL.  

  

serverctrlsp  -  This result parameter will be filled in with an allocated
array of controls copied out of the LDAPMessage message.  The control array
SHOULD be freed by calling ldap\_controls\_free.  If no controls were returned,
\*serverctrlsp is set to NULL.  

  




 **See Also :**


**[ldap\_controls\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA728E830A49FDFD85256F5C00488A7C)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**


**[ldap\_parse\_extended\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3EE87DFBDD63B44A85256F5C00488A73)**


**[ldap\_parse\_sasl\_bind\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3C3015B72365D13285256F5C00488A72)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**


**[LDAP\_RES\_xxx](LDAP_RES_xxx.md)**


**[ldap\_value\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/69925F36F6F9779185256F5C00488A6D)**



----------------------------------------------------------------------------------------------------------


 





