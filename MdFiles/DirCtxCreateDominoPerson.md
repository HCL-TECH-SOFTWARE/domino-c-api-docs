




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
a:link, span.MsoHyperlink
 {color:#0563C1;
 text-decoration:underline;}
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



**DirCtxCreateDominoPerson** **- Create an
in-memory dominoPerson entry.** 


**----------------------------------------------------------------------------------------------------------**



**#include <dirctx.h>**



STATUS
LNPUBLIC **DirCtxCreateDominoPerson(**  

      DIRCTX  hCtx,  

      const char \*name,  

      const char \*lastName,  

      DIRENTRY \*hEntry**);**



**Description :**




Create
an in-memory dominoPerson entry. 


Note that
the entry is not actually written to the directory until a subsequent
DirEntryUpdate()[E:\temp\dir\html\direntry\_8h.html
- 8ebb95936adba73844deb8acbdd86f82](file:///E:/temp/dir/html/direntry_8h.html#8ebb95936adba73844deb8acbdd86f82) operation. This API supports the
promotion of existing non-Domino person entries (typically in an LDAP based
directory) to be full dominoPerson entry. It also supports the creation of a
dominoPerson entry from scratch. 


 


 


**Parameters :**



Input :  

hCtx  -  Directory context for this operation.  

  

name  -  The Notes name of the person to be added, specified in Notes
distinguished name or abbreviated name syntax. An entry by this name must not
exist in domainName.  

  

lastName  -  The last name of the person.  

  

hEntry  -  If non-NULL on input, this indicates that a Person entry in a
non-Domino directory (typically LDAP based) is to be "registered" as
a DominoPerson. The input handle is typically obtained from a previous
DirCtxSearchByName or similar search/lookup/get operation. If NULL on input,
then a new DominoPerson entry will be created from scratch and returned via
this parameter.  

  




Output :  

(routine)  -  Status code:   

NOERROR on success.   

ERR\_DN\_PARSE  

ERR\_DIR\_NULL\_ARGUMENT If itemName is NULL.  

ERR\_DIR\_INVALID\_ARGUMENT  

ERR\_DIR\_MUST\_PROMOTE  

An ERR status on failure indicating the problem.  

  

  

hEntry  -  If non-NULL on input, this indicates that a Person entry in a
non-Domino directory (typically LDAP based) is to be "registered" as
a DominoPerson. The input handle is typically obtained from a previous
DirCtxSearchByName or similar search/lookup/get operation. If NULL on input,
then a new DominoPerson entry will be created from scratch and returned via
this parameter.  

  




 **See Also :**


**[DirEntryUpdate](DirEntryUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





