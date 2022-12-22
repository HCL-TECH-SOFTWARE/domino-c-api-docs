




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



**DirEntryUpdate** **- Update
the in-memory  hEntry object to the directory, committing all the changes that
have been made.**


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC **DirEntryUpdate(**  

      DIRENTRY  hEntry**);**



**Description :**



If the
hEntry was just created with a DirCtxCreateDominoPerson()[E:\temp\dir\html\dirctx\_8h.html
- b4a1ec8fbc41cc902c2d0d8fe994615b](file:///E:/temp/dir/html/dirctx_8h.html#b4a1ec8fbc41cc902c2d0d8fe994615b)[E:\temp\dir\html\dirctx\_8h.html
- c6db69856fc2ef9d5797f367542e2424](file:///E:/temp/dir/html/dirctx_8h.html#c6db69856fc2ef9d5797f367542e2424) operation and the specified
domainName is a Domino directory, then a new entry is created with the
specified DN. If it is an LDAP directory then a new entry is created with the
specified distinguishedName and notesDNs If an entry by the same DN or notesDN
exists in the relevant directory then an error is returned. 


        On
return all changes queued up in the hEntry by item add, delete, replace
operations are cleared so the caller is free to use the same hEntry to make
further changes.


 


**Parameters :**



Input :  

hEntry  -  Handle to the person entry to update.  

  




Output :  

(routine)  -  An ERR status on failure indicating the problem.   

  

  




 **See Also :**


**[DirEntryItemAdd](DirEntryItemAdd.md)**


**[DirEntryItemDelete](DirEntryItemDelete.md)**



----------------------------------------------------------------------------------------------------------


 





