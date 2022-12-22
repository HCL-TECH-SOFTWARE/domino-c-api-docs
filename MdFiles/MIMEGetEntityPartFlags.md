




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



**MIMEGetEntityPartFlags** **- get the
MIME\_PART\_xxx flags for the input entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetEntityPartFlags(**  

      NOTEHANDLE  hNote,  

      PMIMEENTITY  pEntity,  

      DWORD \*pdwFlags**);**



**Description :**



The function
MIMEGetEntityPartFlags returns the MIME\_PART\_xxx flags for the input MIME
entity.  The flags are:


 


MIME\_PART\_HAS\_BOUNDARY                       - part has a
boundary; i.e., it is a child of a multipart entity.


MIME\_PART\_HAS\_HEADERS              - part has
headers; e.g., Content-Type.


MIME\_PART\_BODY\_IN\_DBOBJECT                - part data
is stored in a file attachment


MIME\_PART\_SHARED\_DBOBJECT                 - part data
is stored in an attachment and it is shared with another referrer. (rare
usage.)


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note  

  

pEntity  -  a pointer to current MIME entity (from a MIME directory constructed
from hNote).  

  




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

  

  

  

pdwFlags  -  the returned bit flags; always set to 0 on entry by MIMEGetEntityPartFlags.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DWORD dwFlags;


BOOL bPartHasBoundary;


BOOL bPartHasHeaders;


BOOL
bPartDataInDBObject;


 


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


if (error =
MIMEGetEntityPartFlags(hNote, pRootEntity, &dwFlags)) {


        goto exit;


}


 


bPartHasBoundary    =
(dwFlags & MIME\_PART\_HAS\_BOUNDARY) != 0;


bPartHasHeaders     =
(dwFlags & MIME\_PART\_HAS\_HEADERS) != 0;


bPartDataInDBObject =
(dwFlags & MIME\_PART\_BODY\_IN\_DBOBJECT) != 0;


 


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[MIME\_PART\_xxx](MIME_PART_xxx.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





