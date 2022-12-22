




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



**NSFMimePartCreateStream** **- Creates a
context for streaming a large MIME part to a note item.  All other
NSFMimePart\*Stream functions use this context.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartCreateStream(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      WORD  wPartType,  

      DWORD  dwFlags,  

      DHANDLE \*phCtx**);**



**Description :**



The function
NSFMimePartCreateStream creates a MIME part context for adding large MIME parts
to a named note item.  Subsequent calls to NSFMimePartAppendStream.
NSFMimePartAppendFileToStream, or NSFMimePartAppendFileToStream require the
MIME part context as input.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

pchItemName  -  the name of the item in which to store the appended MIME data.  

  

wItemNameLen  -  the length of the item name.  

  

wPartType  -  the type of MIME part item to create; MIME\_PART\_PROLOG,
MIME\_PART\_BODY, MIME\_PART\_EPILOG, etc.  

  

dwFlags  -   flags for the MIME part; MIME\_PART\_HAS\_BOUNDARY,
MIME\_PART\_HAS\_HEADERS, etc.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully create the MIME part context.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

phCtx  -  a pointer to a location for the output handle to the context.  

  




 **Sample Usage :**


    STATUS error;


DHANDLE hCtx;


 


if (err = NSFMimePartCreateStream(hNote,


                                         
MAIL\_BODY\_ITEM,


                                         
sizeof(MAIL\_BODY\_ITEM)-1,


                                         
MIME\_PART\_BODY,


                                         
MIME\_PART\_HAS\_BOUNDARY | MIME\_PART\_HAS\_HEADERS,


                                         
&hCtx)) {


        goto exit;


}


 


 **See Also :**


**[MIMEPARTTYPE](MIMEPARTTYPE.md)**


**[MIME\_PART\_xxx](MIME_PART_xxx.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[NSFMimePartAppendStream](NSFMimePartAppendStream.md)**


**[NSFMimePartCloseStream](NSFMimePartCloseStream.md)**



----------------------------------------------------------------------------------------------------------


 





