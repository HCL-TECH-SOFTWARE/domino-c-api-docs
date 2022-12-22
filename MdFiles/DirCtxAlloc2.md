




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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 8.5.2**



**Function : Dir**



**DirCtxAlloc2** **- Allocates
a directory context for performing directory operations.** 


**----------------------------------------------------------------------------------------------------------**



**#include <dirctx.h>**



STATUS
LNPUBLIC **DirCtxAlloc2(**  

      const char \*serverName,  

      const char \*domainName,  

      DIRCTX \*rethCtx**);**



**Description :**



The properties
of this directory context are assigned the following values: 


*       
The server name will be assigned from the serverName argument. 


*       
The domain will be assigned from the domainName argument. 


*       
The flags value will be 0.


 


**Parameters :**



Input :  

serverName  -  Name of the Domino server to perform the operation on. A client
would typically specify the directory server for this parameter (see
DirServerGetDirectoryServer()). A server would typically specify NULL to
perform the operation locally.  

  

domainName  -  The Domino domain to determine the administration server for. If
domainName is NULL or the server does not have directory assistance configured,
then the primary domain of serverName is implied.  

  




Output :  

(routine)  -  Status code:   

NOERROR on success.   

ERR\_DIR\_NULL\_ARGUMENT if rethCtx is NULL.   

An ERR status on failure indicating the problem.   

  

  

rethCtx  -  Directory context for directory operations. NULLDIRCTX is returned
if unsuccessful.  

  




 




----------------------------------------------------------------------------------------------------------


 





