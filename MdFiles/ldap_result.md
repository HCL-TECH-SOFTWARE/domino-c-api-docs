




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



**ldap\_result** **- Obtain
the result of a previous asynchronously initiated operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_result(**  

      LDAP \*ld,  

      int  msgid,  

      int  all,  

      struct timeval \*timeout,  

      LDAPMessage \*\*result**);**



**Description :**



This
function is used to obtain the result of a previous asynchronously initiated
operation. 


 


Note that
depending on how it is called, ldap\_result can actually return a list or
"chain" of result messages. The ldap\_result function only returns
messages for a single request, so for all LDAP operations other than search,
only one result message is expected; that is, the only time the "result
chain" can contain more than one message is if results from a search
operation are returned.  Once a chain of messages has been returned to the
caller, it is no longer tied in any caller-visible way to the LDAP request that
produced it.  However, it MAY be tied to the session handle.  Therefore, a
chain of messages returned by calling ldap\_result or by calling a synchronous
search routine will never be affected by subsequent LDAP API calls except for
ldap\_msgfree (which is used to dispose of a chain of messages) and the unbind
calls (which dispose of a session handle): ldap\_unbind, ldap\_unbind\_s, or
ldap\_unbind\_ext, or functions defined by extensions of this API.


 


Implemented
as a macro:


 


#define
ldap\_result(ld, msgid, all, timeout, result)      ND\_ldap\_result((ld), (msgid),
(all), (timeout), (result))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

msgid  -  The message id of the operation whose results are to be returned. 
See LDAP\_RES\_xxx.  

  

all  -  Specifies how many messages will be retrieved in a single call  to
ldap\_result.  This parameter only has meaning for search results.  See
LDAP\_MSG\_xxx.  

  

timeout  -  A timeout specifying how long to wait for results to be returned. 
A NULL value causes ldap\_result to block until results are available.  A
timeout value of zero seconds specifies a polling behavior.  

  




Output :  

(routine)  -  0 - If the timeout expired.   

  

-1 - If an error occurs, in which case the error parameters of the LDAP session
handle will be set accordingly.  

  

  

result  -  A result parameter that will contain the result(s) of the
operation.  See LDAP\_RES\_xxx.  If an API error occurs or no results are
returned, \*result is set to NULL.  

  




 **See Also :**


**[ldap\_msgfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ACE588BDB8F4BD8C85256F5C00488A70)**


**[ldap\_msgid](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E912825DE531A38285256F5C00488A75)**


**[ldap\_msgtype](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/24DD9BFD3ECF196785256F5C00488A74)**


**[LDAP\_MSG\_xxx](LDAP_MSG_xxx.md)**


**[LDAP\_RES\_xxx](LDAP_RES_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





