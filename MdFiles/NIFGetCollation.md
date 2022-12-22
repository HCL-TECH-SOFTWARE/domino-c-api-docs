




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



**Function : Views**



**NIFGetCollation** **- Get
current collation for a collection.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFGetCollation(**  

      HCOLLECTION  hCollection,  

      WORD \*retCollationNum**);**



**Description :**



Beginning
with Release 4, more than one collation may be defined for a view or folder.  A
collation is a set of columns and sort specifications that determines how the
view or folder will be sorted.  


 


When a
collection is first opened, its current collation is set to 0.


 


**Parameters :**



Input :  

hCollection  -  Handle to the open collection.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Successfully retrieved Collation information.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

retCollationNum  -  Word containing the Collation Number.  

  




 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFSetCollation](NIFSetCollation.md)**



----------------------------------------------------------------------------------------------------------


 





