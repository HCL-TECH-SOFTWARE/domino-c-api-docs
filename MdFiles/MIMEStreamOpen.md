




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



**MIMEStreamOpen** **- Open a
MIME Stream for a MIME format note.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEStreamOpen(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      DWORD  dwOpenFlags,  

      MIMEHANDLE \*rethMIMEStream**);**



**Description :**



This
function MIMEStreamOpen opens a MIME stream for MIME format note.  You must
specify as input the handle to the open note, the name of the item to use to
create the MIME stream, the length of the item name, the MIME stream open flags
(see the MIME\_STREAM\_XXX flags), and a pointer to a MIMEHANDLE.  The MIMEHANDLE
must be used on all subsequent calls to MIMEStream APIs.


 


On entry
MIMEStreamOpen always writes a NULL to the output MIME handle location,
\*rethMIMEStream.  


 


If the flag
MIME\_STREAM\_OPEN\_READ is specified, MIMEStreamOpen creates a MIME stream,
serializes the named items into it, and returns a MIMEHANDLE to the MIME
stream.  Specify the flag MIME\_STREAM\_RFC2822\_INCLUDE\_HEADERS to flush all
RFC2822 headers to the output MIME stream; i.e., the message's initial headers
-- To, From, Subject, Date, etc.  Also specify the flag
MIME\_STREAM\_OPEN\_INCLUDE\_HEADERS to flush all MIME entity headers to the output
MIME stream.


 


If the flag
MIME\_STREAM\_OPEN\_WRITE is specified, MIMEStreamOpen ignores the pchItemName and
wItemNameLen arguments.  MIMEStreamOpen creates a MIME stream and returns a
MIMEHANDLE to the MIME stream.  (After completing output to the MIME stream
using MIMEStreamPutLine or MIMEStreamWrite, specify the item name and its
length on the subsequent call to MIMEStreamItemize.)


 


(N.B.  It is
an error to specify both the MIME\_STREAM\_OPEN\_READ and MIME\_STREAM\_OPEN\_WRITE
flags.  If both are specified, MIMEStreamOpen behaves as if only
MIME\_STREAM\_OPEN\_READ was specified.)


 


 


**Parameters :**



Input :  

hNote  -  Handle to the open note  

  

pchItemName  -  Pointer to the item name (does not have to be an ASCIIZ
string).  

  

wItemNameLen  -  The length of item name  

  

dwOpenFlags  -  MIME Stream open flags  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the note.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

rethMIMEStream  -  Pointer to a MIME stream handle.  

  




 **Sample Usage :**


STATUS error;


MIMEHANDLE hMIMEStream;


 


if (error =
MIMEStreamOpen(hNote,


                                
MAIL\_BODY\_ITEM,


                                
sizeof(MAIL\_BODY\_ITEM)-1,


                                
MIME\_STREAM\_OPEN\_READ|MIME\_STREAM\_INCLUDE\_HEADERS,


                                
&hMIMEStream)) {


        goto exit;


}


 


 **See Also :**


**[MIMEHANDLE](MIMEHANDLE.md)**


**[MIMEStreamClose](MIMEStreamClose.md)**


**[MIMEStreamRead](MIMEStreamRead.md)**


**[MIMEStreamWrite](MIMEStreamWrite.md)**


**[MIME\_STREAM\_xxx](MIME_STREAM_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





