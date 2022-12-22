




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
 {font-family:"Microsoft Sans Serif";
 panose-1:2 11 6 4 2 2 2 2 2 4;}
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




**Initial Release 7.0.2**



**Function : MIME**



**MIMEGetEntityDataSize** **- Get the
data size for a MIME entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetEntityDataSize(**  

      NOTEHANDLE  hNote,  

      PMIMEENTITY  pME,  

      WORD  wDataType,  

      DWORD \*pdwDataLen**);**



**Description :**



This is a simplification of MIMEGetEntityData.  Its definition 
is:


 


         #define MIMEGetEntityDataSize(hNote, pME, wDataType,
pdwDataLen)            MIMEGetEntityData((hNote), (pME), (wDataType), NULL,
MAXDWORD, NULL, (pdwDataLen))


 


        See the MIMEGetEntityData for more detail.


 


**Parameters :**



Input :  

hNote  -  a handle to an open note  

  

pME  -  a pointer to current MIME entity (from a MIME directory constructed
from hNote).  

  

wDataType  -  what to get -- boundary, headers, body or all.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the
parameter value memory.  

     ERR\_MISC\_INVALID\_ARGS - returned for various input parameter errors.  

     ERR\_MIME\_NO\_DATA - returned if no MIME data for input entity or if no data
at requested offset.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

pdwDataLen  -  pointer to location for number of bytes in requested MIME entity
data.  

  




 **See Also :**


**[MIMEGetEntityData](MIMEGetEntityData.md)**


**[MIME\_ENTITY\_DATA\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/7663712078DB484548257192001F16BA)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





