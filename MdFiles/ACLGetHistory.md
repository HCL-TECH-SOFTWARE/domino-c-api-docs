




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



**ACLGetHistory** **- Return
handle to buffer containing change history strings**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLGetHistory(**  

      DHANDLE  hACL,  

      DHANDLE far \*hHistory,  

      WORD far \*HistoryCount**);**



**Description :**



Allocate a
buffer and read the change history for this access control list into the
buffer.  The buffer will contain LMBCS strings, one entry for each change
history event.  Each LMBCS string is terminated by two NULL characters, for
example LastString\0\0PreviousString\0\0.  The strings appear in LIFO (last in,
first out) order.  The number of strings in the buffer is returned at
\*retHistoryCount.  If there is no change history for this ACL, the
retHistoryCount will be 0 and the buffer handle will be NULLHANDLE.  If there
are any history strings, the handle to the buffer is returned;  the caller is
responsible for freeing this memory by calling OSMemFree().


 


**Parameters :**



Input :  

hACL  -  Handle of the ACL.  

  




Output :  

(routine)  -  NOERROR - Successfully retrieved history.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

hHistory  -  Handle of memory containing the change history (or NULLHANDLE if
there are no change history strings).  

  

HistoryCount  -  Number of strings in the change history (0 if there are no
change history strings).  

  




 **See Also :**


**[NSFDbReadACL](NSFDbReadACL.md)**



----------------------------------------------------------------------------------------------------------


 





