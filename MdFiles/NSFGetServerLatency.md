




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



**Function : Statistics Reporting**



**NSFGetServerLatency** **- Estimate
the time required to access a server.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetServerLatency(**  

      char far \*ServerName,  

      DWORD  Timeout,  

      DWORD far \*retClientToServerMS,  

      DWORD far \*retServerToClientMS,  

      WORD far \*ServerVersion**);**



**Description :**



This
function returns estimates of how many milliseconds are required to send a
message to the named server, and how long it takes for a reply from that
server.  This function can also be used to obtain the version number of the
server.


 


**Parameters :**



Input :  

ServerName  -  Null-terminated string containing the name of the server to
query.  

  

Timeout  -  Number of milliseconds to wait for a reply from the server.  A
timeout of 0 indicates that the default timeout value is to be used.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

retClientToServerMS  -  Optional - If not NULL, the number of milliseconds
required to send the request to the server is stored at this address.  

  

retServerToClientMS  -  Optional - If not NULL, the number of milliseconds
required for the reply to return from the server is stored at this address.  

  

ServerVersion  -  Optional - If not NULL, the server version (the Domino build
number for the server) is stored at this address.  

  




 **See Also :**


**[NSFGetServerStats](NSFGetServerStats.md)**



----------------------------------------------------------------------------------------------------------


 





