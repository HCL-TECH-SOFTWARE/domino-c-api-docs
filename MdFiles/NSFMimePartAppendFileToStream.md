




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



**NSFMimePartAppendFileToStream** **- Append
data from a file to a MIME part context.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartAppendFileToStream(**  

      DHANDLE  hCtx,  

      char \*pszFilename**);**



**Description :**



The function
NSFMimePartAppendFileToStream opens the named input file and appends its data
to the MIME part context using the supplied MIME part context handle.  Note
that the data is **always** base64 encoded as it is written to the MIME part
context and that the caller is responsible for appending any MIME part boundary
or headers to the MIME part context before calling
NSFMimePartAppendFileToStream.


 


 


**Parameters :**



Input :  

hCtx  -  the handle to the MIME part context.  

  

pszFilename  -  the name of the file from which to append data to the MIME part
context.  

  




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
base64\015\012"


                        "Content-Disposition:
inline\015\012";


 


if (error =
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
NSFMimePartAppendFileToStream(hCtx, "picture.jpg")) {


        goto exit;


}


 


if (error =
NSFMimePartCloseStream(hCtx, TRUE)) {


        goto exit;


}


 


 




----------------------------------------------------------------------------------------------------------


 





