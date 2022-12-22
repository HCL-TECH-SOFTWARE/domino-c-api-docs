




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



**NSFMimePartAppend** **- Adds a
TYPE\_MIME\_PART item to a note**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartAppend(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      WORD  wPartType,  

      DWORD  dwFlags,  

      char \*pchPart,  

      WORD  wPartLen**);**



**Description :**



The function
NSFMimePartAppend adds a TYPE\_MIME\_PART item to an open note.  The
TYPE\_MIME\_PART item begins with a MIME\_PART ODS structure (see MIME\_PART in
mimeods.h) and is followed by the part data.  The part data may consist of a
boundary, headers, and the part 'body'.  If the caller is adding a part with a
boundary or headers, the bit flags MIME\_PART\_HAS\_BOUNDARY and
MIME\_PART\_HAS\_HEADERS, respectively, should be set in the dwFlags argument.


 


If the part
is a multipart type --e.g., 'Content-type: multipart/mixed;
boundary="\_\_BoundaryString\_\_"'-- wPartType should be set to
MIME\_PART\_PROLOG.


 


If the part
is a message type --e.g., 'Content-type: message/rfc822'-- wPartType should be
set to MIME\_PART\_MESSAGE.


 


If the part
is only a terminating boundary (e.g. '--\_\_BoundaryString\_\_--'), wPartType
should be set to MIME\_PART\_EPILOG.


 


If the part
is a typical MIME part (e.g., 'Content-type: text/plain'), wPartType should be
set to MIME\_PART\_BODY.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

pchItemName  -  Pointer to buffer containing item name to use; typically should
be MAIL\_BODY\_ITEM.  

  

wItemNameLen  -  item name length.  

  

wPartType  -  the type of MIME part to add.  

  

dwFlags  -  flags that describe the MIME part -- has headers, has  boundary,
etc.  

  

pchPart  -  pointer to the part data to add.  

  

wPartLen  -   the part data length in bytes.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully added the MIME part.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


#define HEADERS
"Content-type: text/plain;
charset=\"us-ascii\"\015\012\015\012"


#define BODY "This
is a text plain part.\015\012"


#define PARTLEN
((sizeof(HEADERS)-1)+(sizeof(BODY)-1))


 


STATUS error;


char
achPart[PARTLEN+1];


 


strcpy(achPart,
HEADERS);


strcat(achPart, BODY);


 


error =
NSFMimePartAppend(hNote,


                               
MAIL\_BODY\_ITEM,


                               
sizeof(MAIL\_BODY\_ITEM)-1,


                               
MIME\_PART\_BODY,


                               
MIME\_PART\_HAS\_HEADERS,


                               
achPart,


                               
PARTLEN);


if (error) {


        goto exit;


}


 


 **See Also :**


**[MIMEPARTTYPE](MIMEPARTTYPE.md)**


**[MIME\_PART\_xxx](MIME_PART_xxx.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[NSFMimePartDelete](NSFMimePartDelete.md)**



----------------------------------------------------------------------------------------------------------


 





