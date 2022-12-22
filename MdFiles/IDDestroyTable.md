




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



**Function : ID Table**



**IDDestroyTable** **- Free all
memory associated with an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDDestroyTable(**  

      DHANDLE  hTable**);**



**Description :**



This
function deallocates all memory associated with an ID Table. Use this function
instead of OSMemFree to free the ID Table's memory.


 


**Parameters :**



Input :  

hTable  -  The handle of the ID Table structure that is to be destroyed.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - If ID Table was successfully destroyed.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**



----------------------------------------------------------------------------------------------------------


 





