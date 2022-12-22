




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
-->




**Initial Release 7.0.2**



**Function : MIME**



**MIMEGetDecodedEntityData** **- get
decoded body of input MIME entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetDecodedEntityData(**  

      DHANDLE  hNote,  

      PMIMEENTITY  pMimeEntity,  

      DWORD  dwEncodedOffset,  

      DWORD  dwChunkLen,  

      DHANDLE \*phData,  

      DWORD \*pdwDecodedDataLen,  

      DWORD \*pdwEncodedDataLen**);**



**Description :**



This
function MIMEGetDecodedEntityData returns the requested MIME data for the input
MIME entity by allocating a memory block for the data, copying the data to the
block, and returning a handle to the allocated block.  Note that the caller is
responsible for freeing the returned memory block.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note  

  

pMimeEntity  -  a pointer to current MIME entity (from a MIME directory
constructed from hNote).  

  

dwEncodedOffset  -  offset into the encoded MIME entity; should be 0 initially.  

  

dwChunkLen  -  number of bytes to return in allocated block (see phData below).  

  




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

  

pdwDecodedDataLen  -  pointer to location for number of decoded bytes returned
for requested MIME entity data.  

  

pdwEncodedDataLen  -  pointer to location for number of encoded bytes processed
in requested MIME entity data.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DWORD dwEncodedOffset =
0;


DWORD dwChunkLen =
1024;


DHANDLE hData;


DWORD dwDecodedDataLen;


DWORD dwEncodedDataLen;


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
MIMEGetDecodedEntityData(hNote


                                                      pRootEntity,


                                                      dwEncodedOffset,


                                                      dwChunkLen,


                                                      &hData,


                                                      &dwDecodedDataLen,


                                                      &dwEncodedDataLen))
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


 


        dwEncodedOffset
+= dwEncodedDataLen;


        OSUnlockAndFree(hData);


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 




----------------------------------------------------------------------------------------------------------


 





