




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




**Initial Release 4.0**



**Function : Access Control List**



**ACLGetFlags** **- Return
flags that apply to the entire ACL.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLGetFlags(**  

      DHANDLE  hACL,  

      DWORD far \*Flags**);**



**Description :**



Return the
DWORD of flags that apply to this whole access control list.


 


**Parameters :**



Input :  

hACL  -  Handle of the access control list.  

  




Output :  

(routine)  -  NOERROR - Successfully retrieved flags  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

  

Flags  -  ACL-wide flags.  

  




 **See Also :**


**[ACLSetFlags](ACLSetFlags.md)**


**[ACL\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/6AF0458CF99F0045852561CE005E4CC5)**



----------------------------------------------------------------------------------------------------------


 





