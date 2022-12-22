




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



**NSFMimePartAppendStream** **- Appends
data to a MIME part item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartAppendStream(**  

      DHANDLE  hCtx,  

      char \*pchData,  

      WORD  wDataLen**);**



**Description :**



The function
NSFMimePartAppendStream appends the data pointed to by pchData to the MIME part
context created by NSFMimePartCreateStream.  NSFMimePartCloseStream must be
called to "flush" the context to the item originally specified on the
calls to NSFMimePartCreateStream.  In addition NSFMimePartCloseStream frees all
memory associated with the MIME part context.


 


N.B., When
line endings are used --e.g., with boundary lines or headers-- the line ending **must**
be carriage return, line feed, ASCII values 13 and 10, respectively. 
NSFMimePartAppendStream will not function correctly if UNIX (line feed) or Mac
(carriage return) line endings are used.


 


 


**Parameters :**



Input :  

hCtx  -  the handle to the MIME part context.  

  

pchData  -  pointer to the data to append to the MIME part context.  

  

wDataLen  -  the length of the data.  

  




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
NSFMimePartAppendStream(hCtx, pszBoundary, strlen(pszBoundary)) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszHeaders, strlen(pszHeaders)) {


        goto exit;


}


 


if (error =
NSFMimePartAppendStream(hCtx, pszBody, strlen(pszBody)) {


        goto exit;


}


 


 **See Also :**


**[NSFMimePartCloseStream](NSFMimePartCloseStream.md)**


**[NSFMimePartCreateStream](NSFMimePartCreateStream.md)**



----------------------------------------------------------------------------------------------------------


 





