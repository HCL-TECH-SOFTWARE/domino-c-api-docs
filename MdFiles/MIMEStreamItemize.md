




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



**MIMEStreamItemize** **- Parse a
MIME stream to create a Notes/Domino MIME format document.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEStreamItemize(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      DWORD  dwFlags,  

      MIMEHANDLE  hMIMEStream**);**



**Description :**



This
function MIMEStreamItemize parses a MIME stream to create a Notes/Domino MIME
format document.  You must specify as input a handle to an open note,
optionally an item name to received the "itemized" MIME body parts,
the length of the item name, the itemize flags, and the handle to the MIME
stream.


 


If the
dwFlags variable is 0, MIMEStreamItemize only itemizes the body parts of the
input MIME stream.  If the pchItemName pointer is NULL or if pchItemName is
equal to the null string (""), MIMEStreamItemize itemizes the MIME
body parts into items named "Body".  If the dwFlags variable is set
to MIME\_STREAM\_ITEMIZE headers, MIMEStreamItemize only parses and itemizes the
MIME streams initial RFC2822 headers into Notes/Domino items; e.g., the
Internet message header, 'To:', is itemized to the Notes item, 'SendTo'.


 


MIMEStreamItemize
itemizes the headers and the body parts of the input MIME stream if both the
MIME\_STREAM\_ITEMIZE\_HEADERS and MIME\_STREAM\_ITEMIZE\_BODY flags are set in
dwFlags.  (See the MIME\_STREAM\_ITEMIZE\_XXX flags, especially MIME\_STREAM\_ITEMIZE\_FULL.)


 


 


**Parameters :**



Input :  

hNote  -  A handle to an open note.  

  

pchItemName  -  An optional pointer to an item name.  

  

wItemNameLen  -  The length of the item name.  

  

dwFlags  -   The MIME stream itemize flags.  

  

hMIMEStream  -  A handle to the MIME stream.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the note.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the user.  

  

  

  




 **Sample Usage :**


STATUS error;


 


if (error =
MIMEStreamItemize(hNote, MAIL\_BODY\_ITEM, sizeof(MAIL\_BODY\_ITEM)-1,
MIME\_STREAM\_ITEMIZE\_FULL, hMIMEStream)) {


        goto exit;


}


 


 **See Also :**


**[MIMEStreamPutLine](MIMEStreamPutLine.md)**


**[MIME\_STREAM\_xxx](MIME_STREAM_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





