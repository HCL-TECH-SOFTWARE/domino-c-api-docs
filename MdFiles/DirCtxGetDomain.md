




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




**Initial Release 8.5.2**



**Function : Dir**



**DirCtxGetDomain** **- Gets the
name of the Domino domain to perform directory operations on.**


**----------------------------------------------------------------------------------------------------------**



**#include <dirctx.h>**



STATUS
LNPUBLIC **DirCtxGetDomain(**  

      DIRCTX  hCtx,  

      char \*domainName**);**



**Description :**



Gets the
name of the Domino domain to perform directory operations on, if not previously
set then a NULL domain name is returned (i.e. "").


 


**Parameters :**



Input :  

hCtx  -  Directory context to be queried.  

  




Output :  

(routine)  -  Status code:   

NOERROR on success.   

An ERR status on failure indicating the problem.   

  

  

domainName  -  Caller allocated buffer at least MAXDOMAINNAME+1 in size to
receive the domain component of the hCtx.  

  




 **See Also :**


**[DirCtxGetDirectoryServer](DirCtxGetDirectoryServer.md)**



----------------------------------------------------------------------------------------------------------


 





