




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



**NSFMimePartAppendObjectToStream** **- Associates
a named database object (i.e., a file attachment) with the given MIME part
context.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartAppendObjectToStream(**  

      DHANDLE  hCtx,  

      char \*pszAttachmentName**);**



**Description :**



The function
NSFMimePartAppendObjectToStream associates a named attachment with the given
MIME part stream.  Assumptions:


 


*       
You have previously called NSFMimePartAppendStream to add the
boundary, headers, and trailing CRLF to the MIME part.


*       
You have previously specified the appropriate
Content-Transfer-Encoding header.  If the named attachment is not encoded,
specify "binary" encoding.


*       
You should not call NSFMimePartAppendStream after
NSFMimePartAppendObjectToStream. The next MimePartStream call should be
NSFMimePartCloseStream.


 


**Parameters :**



Input :  

hCtx  -  the handle to the MIME part context.  

  

pszAttachmentName  -  the name of the database object (i.e., file attachment)
from which to append data to the MIME part context.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully appended the data to the MIME part context..  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


STATUS error;


DHANDLE hCtx;


char \*pszBoundary =
"\015\012--Boundary\_String\015\012";


char \*pszHeaders =
"Content-type: image/jpeg\015\012"


                        "Content-Transfer-Encoding:
binary\015\012"


                        "Content-Disposition:
inline\015\012";


 


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
NSFMimePartAppendStream(hCtx, pszBoundary, strlen(pszBoundary)) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszHeaders, strlen(pszHeaders)) {


        goto exit;


}


 


if (error =
NSFMimePartAppendObjectToStream(hCtx, "picture.jpg") {


        goto exit;


}


 


if (error =
NSFMimePartCloseStream(hCtx, TRUE)) {


        goto exit;


}


 


 **See Also :**


**[NSFMimePartAppend](NSFMimePartAppend.md)**


**[NSFMimePartAppendFileToStream](NSFMimePartAppendFileToStream.md)**


**[NSFMimePartCloseStream](NSFMimePartCloseStream.md)**


**[NSFMimePartCreateStream](NSFMimePartCreateStream.md)**



----------------------------------------------------------------------------------------------------------


 





