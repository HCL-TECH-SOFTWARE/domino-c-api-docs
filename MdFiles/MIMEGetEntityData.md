




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 7.0.2**



**Function : MIME**



**MIMEGetEntityData** **- get the
data for a MIME entity.  May fetch boundary, headers, and body separately or
all together.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetEntityData(**  

      NOTEHANDLE  hNote,  

      PMIMEENTITY  pME,  

      WORD  wDataType,  

      DWORD  dwOffset,  

      DWORD  dwOffset,  

      DHANDLE \*phData,  

      DWORD \*pdwDataLen**);**



**Description :**



This
function MIMEGetEntityData returns the requested MIME data for the input MIME
entity by allocating a memory block for the data, copying the data to the
block, and returning a handle to the allocated block.  Note that the caller is
responsible for freeing the returned memory block and that the MIME entity data
is returned in its original encoding; e.g., as base64 encoded data.


 


The caller
may use the wDataType argument to specify which elements of the MIME entity
data MIMEGetEntityData should return:


 


*       
MIME\_ENTITY\_DATA\_BOUNDARY - Get boundary only.


*       
MIME\_ENTITY\_DATA\_HEADERS - Get headers only.


*       
MIME\_ENTITY\_DATA\_BODY - Get body only.


*       
MIME\_ENTITY\_DATA\_RFC822TEXT - Get boundary, headers and body


 


**Parameters :**



Input :  

hNote  -  a handle to an open note  

  

pME  -  a pointer to current MIME entity (from a MIME directory constructed
from hNote).  

  

wDataType  -  what to get -- boundary, headers, body or all.  

  

dwOffset  -  offset into MIME entity; should be 0 initially.  

  

dwOffset  -  number of bytes to return in allocated block (see phData below).  

  




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

  

  

  

phData  -  pointer to location for handle to allocated block of MIME entity
data.  NULL is allowed in which case only the size of the requested data is
returned.  

  

pdwDataLen  -  pointer to location for number of bytes in requested MIME entity
data.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DWORD dwOffset = 0;


DWORD dwChunkLen =
1024;


DHANDLE hData;


DWORD dwDataLen;


char \*pData;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


while (TRUE) {


        if (error =
MIMEGetEntityData(hNote


                                             pRootEntity,


                                             MIME\_ENTITY\_DATA\_RFC822TEXT,


                                             dwOffset,


                                             dwChunkLen,


                                             &hData,


                                             &dwDataLen))
{


               if
(error == ERR\_NO\_MIME\_DATA) {


                       break;


               }


               goto
exit;


        }


 


        pData =
OSLock(char, hData);


 


        /\* write data
to file


           ...


        \*/


 


        dwOffset +=
dwDataLen;


        OSUnlockAndFree(hData);


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[MIME\_ENTITY\_DATA\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/7663712078DB484548257192001F16BA)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





