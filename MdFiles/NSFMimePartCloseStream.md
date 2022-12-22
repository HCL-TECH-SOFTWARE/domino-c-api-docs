




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



**NSFMimePartCloseStream** **- Flush a
MIME part context's data to a MIME part item and release all memory associated
with the MIME part context.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartCloseStream(**  

      DHANDLE  hCtx,  

      BOOL  bUpdate**);**



**Description :**



The function
NSFMimePartCloseStream flushes the MIME part context's data to a MIME part item
and releases all memory associated with the MIME part context.  If bUpdate is
FALSE (e.g., if closing the stream after some processing error),
NSFMimePartCloseStream does not create the indicated MIME part item and it only
frees the memory associated with the MIME part context.  The caller must set
bUpdate to TRUE to force NSFMimePartCloseStream to create the indicated MIME
part.


 


 


**Parameters :**



Input :  

hCtx  -  a handle to the MIME part context.  

  

bUpdate  -  if TRUE, create the indicated MIME part note item and free memory,
otherwise only free memory.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully updated the note and closed the MIME part stream.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


STATUS error;


DHANDLE hCtx;


char \*pszBoundary =
"\015\012--Boundary\_String\015\012";


char \*pszHeaders =
"Content-type: text/plain\015\012\015\012";


char \*pszBody =
"This is the body of a text/plain MIME part.\015\012";


 


if (err =
NSFMimePartCreateStream(hNote,


                                         
MAIL\_BODY\_ITEM,


                                         
sizeof(MAIL\_BODY\_ITEM)-1,


                                         
MIME\_PART\_BODY,


                                         
MIME\_PART\_HAS\_BOUNDARY | MIME\_PART\_HAS\_HEADERS,


                                         
&hCtx)) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszBoundary, strlen(pszBoundary))) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszHeaders, strlen(pszHeaders))) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszBody, strlen(pszBody))) {


        goto exit;


}


 


if (error =
NSFMimePartCloseStream(hCtx, TRUE)) {


        goto exit;


}


 


 **See Also :**


**[NSFMimePartAppendStream](NSFMimePartAppendStream.md)**


**[NSFMimePartCreateStream](NSFMimePartCreateStream.md)**



----------------------------------------------------------------------------------------------------------


 





