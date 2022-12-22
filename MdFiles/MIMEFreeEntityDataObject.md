




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



**MIMEFreeEntityDataObject** **- free the
database object (i.e., file attachment) which contains entity's MIME data.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEFreeEntityDataObject(**  

      NOTEHANDLE  hNote,  

      PMIMEENTITY  pEntity**);**



**Description :**



If the input
MIME entity's data is stored in a database object (i.e., a file attachment),
the function MIMEFreeEntityDataObject deletes the $FILE item and associated
database object for the MIME entity without deleting the MIME entity's item. 
If the MIME entity's data is not stored in a database object, the function does
nothing.


 


 


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

  

  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DWORD dwFlags;


 


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


 


if ((dwFlags &
(MIME\_PART\_BODY\_IN\_DBOBJECT|MIME\_PART\_SHARED\_DBOBJECT)) ==
MIME\_PART\_BODY\_IN\_DBOBJECT) {


        if (error =
MIMEFreeEntityDataObject(hNote, pRootEntity)) {


               goto
exit;


        }


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


 


 **See Also :**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





