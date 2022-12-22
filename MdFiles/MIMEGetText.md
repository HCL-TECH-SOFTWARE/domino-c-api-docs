




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



**MIMEGetText** **- get the
MIME text for a given item name.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetText(**  

      NOTEHANDLE  hNote,  

      const char \*pchItemName,  

      WORD  wItemNameLen,  

      BOOL  bNotesEOL,  

      char \*pchBuf,  

      DWORD  dwMaxBufLen,  

      DWORD \*pdwBufLen**);**



**Description :**



The function
MIMEGetText returns the text data from a MIME format note, up to the limit
specified by dwMaxBufLen.  The item name typically should be MAIL\_BODY\_ITEM. 
If the boolean bNotesEOL is TRUE, MIMEGetText will terminate lines using the
Notes line terminator -- the NUL byte, '\0'.


 


MIMEGetText
creates a MIME directory and traverses it searching for text parts. 
MIMEGetText copies most text/\* parts "as is" to the output buffer,
pchBuf, but it 'filters' text/html parts, removing all HTML tags and writing
only the renderable text to the output buffer.  MIMEGetText stores the number
of bytes it wrote to the output buffer in the DWORD pointed to by pdwBufLen.


 


Note that
MIMEGetText only processes the first text part found within a
multipart/alternative, skipping any subsequent parts in the
multipart/alternative.


 


(Note:  This
procedure is essentially the same procedure used by the @Abstract function when
it abstracts MIME documents.)


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note  

  

pchItemName  -  pointer to the item name for the MIME entities; typically
MAIL\_BODY\_ITEM.  

  

wItemNameLen  -  the length of the item name in bytes.  

  

bNotesEOL  -  if TRUE, use Notes line terminators (NUL) at the end of lines;
otherwise use carriage return, line feed.  

  

dwMaxBufLen  -  the maximum number of bytes to write to the output buffer.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the
parameter value memory.  

     ERR\_MISC\_INVALID\_ARGS - returned for various input parameter errors.  

     ERR\_MIME\_NO\_DATA - returned if no MIME data for input item.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

pchBuf  -  pointer to the output buffer.  

  

pdwBufLen  -  pointer to a DWORD for the number of bytes written to the output
buffer.  

  




 **Sample Usage :**


#define MAXBUFLEN 512


 


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DWORD dwFlags;


char achBuf[MAXBUFLEN];


BOOL bNotesEOL = FALSE;


DWORD dwBufLen;


 


if (error =
MIMEGetText(hNote,


                              MAIL\_BODY\_ITEM,


                              sizeof(MAIL\_BODY\_ITEM)-1,


                              bNotesEOL,


                              achBuf,


                              MAXBUFLEN,


                              &dwBufLen))


        goto exit;


}


 


 **See Also :**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[ITEM\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**



----------------------------------------------------------------------------------------------------------


 





