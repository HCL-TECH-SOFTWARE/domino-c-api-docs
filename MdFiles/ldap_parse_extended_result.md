




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



**ldap\_parse\_extended\_result** **- Check for
an error of an asynchronous function.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_parse\_extended\_result(**  

      LDAP \*ld,  

      LDAPMessage \*res,  

      char \*\*resultoidp,  

      struct berval \*\*resultdata,  

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
ldap\_parse\_extended\_result(ld, res, resultoidp, resultdata, freeit) \  

              ND\_ldap\_parse\_extended\_result ((ld), (res), (resultoidp),
(resultdata), (freeit))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

res  -  The result of an LDAP operation as returned by ldap\_result or one of
the synchronous API operation calls.  

  

resultoidp  -  NULL, to ignore this field.  

  

resultdata  -  NULL, to ignore this field.  

  

freeit  -  A boolean that determines whether the result parameter is  disposed
of or not.  If freeit is non-zero, the entire chain of messages represented by
result is disposed of after extracting the requested information. This is
provided as a convenience; zero can also be passed, to not free the messages,
and ldap\_msgfree can be used to free the result later.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

resultoidp  -  The dotted-OID text representation of the name of the extended
operation response.  This string SHOULD be disposed of by calling
ldap\_memfree.  If no OID was returned,  \*resultoidp is set to NULL.  

  

resultdata  -  A pointer to a struct berval containing the data in the extended
operation response.  It SHOULD be disposed of by calling ber\_bvfree.  If no
data is returned, \*resultdatap is set to NULL.  

  




 **See Also :**


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**


**[ldap\_parse\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E8CA6F020C2423F385256F5C00488A71)**


**[ldap\_parse\_sasl\_bind\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3C3015B72365D13285256F5C00488A72)**



----------------------------------------------------------------------------------------------------------


 





