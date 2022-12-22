




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




**Initial Release 7.0**



**Function : Database; DB2**



**NSFGetNSFDB2GroupProperty** **-  Retrieve
DB2-related information about a Domino server**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetNSFDB2GroupProperty(**  

      const char \*group,  

      DWORD  infotype,  

      void far \*buffer,  

      DWORD \*size**);**



**Description :**



This
function retrieves DB2-related information about a Domino server.  This
function is passed the name of a nsfdb2 group,  an identifier for the
information you wish to obtain, the address of a buffer into which the
requested data will be returned, and the address of a size variable.


 


 


**Parameters :**



Input :  

group  -  name of the nsfdb2 group.  

  

infotype  -  specifies a #define from the following:
DB2NSF\_GROUP\_PROPERTY\_CLASS  

  

  

size  -  specifies the size of buffer  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successful.  

  

ERR\_DB2NSF\_BUFFER\_TOO\_SMALL  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

buffer  -  points to a caller supplied variable / buffer.  

  

size  -  returns the size in bytes of the data returned.   

 if STATUS==ERR\_DB2NSF\_BUFFER\_TOO\_SMALL, returns the required size of the
buffer  

  




 **See Also :**


**[NSFDB2GetInfo](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**



----------------------------------------------------------------------------------------------------------


 





