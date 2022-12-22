




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



**NSFIsMimePartInFile** **- Given a
MIME part, check it to see if it's content is in a file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



BOOL
LNPUBLIC **NSFIsMimePartInFile(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhMIMEItem,  

      char \*pchFileName,  

      WORD  wMaxFileNameLen**);**



**Description :**



Given a
BLOCKID for a MIME part item, the function  NSFIsMimePartInFile returns TRUE if
the MIME part item's data is stored in a file attachment, FALSE if the MIME
part item's data is stored inline within the MIME part item.  If NSFIsMimePartInFile
returns TRUE, it also optionally writes the file attachment's file name to the
output buffer, pchFileName.  The caller may pass NULL for pchFileName if it
does need the file name.


 


Note:  If
the file name length is greater than wMaxFileNameLen, NSFIsMimePartInFile does
not write any data to the output buffer and it returns FALSE.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

bhMIMEItem  -  BLOCKID of a MIME part item.  

  

wMaxFileNameLen  -  maximum length of the output file name.  

  




Output :  

(routine)  -  TRUE if the MIME part item data is contained in a file
attachment.  

  

  

pchFileName  -  the name of the file containing the MIME part item's data (if
functions returns TRUE); may be NULL.  

  




 **Sample Usage :**


#define MAXFILENAMELEN
512


 


STATUS error;


BLOCKID bhMIMEItem;


BOOL bMimeDataInFile;


char
pchFileName[MAXFILENAMELEN];


 


if (error =
NSFItemInfo(hNote,


                              MAIL\_BODY\_ITEM,


                              sizeof(MAIL\_BODY\_ITEM)-1,


                              &bhMIMEItem,


                              NULL,


                              NULL,


                              NULL))
{


        goto exit;


}


 


bMimeDataInFile =
NSFIsFileItemMimePart(hNote, bhMIMEItem, pchFileName, MAXFILENAMELEN );


 


 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NSFItemInfo](NSFItemInfo.md)**



----------------------------------------------------------------------------------------------------------


 





