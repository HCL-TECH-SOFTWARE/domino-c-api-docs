




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Mail Gateway**



**MailGetMessageAttachmentInfo** **- Returns
information regarding an attachment of a mail message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



BOOL
LNPUBLIC **MailGetMessageAttachmentInfo(**  

      DHANDLE  hMessage,  

      WORD  Num,  

      BLOCKID far \*bhItem,  

      char far \*FileName,  

      DWORD far \*FileSize,  

      WORD far \*FileAttributes,  

      WORD far \*FileHostType,  

      TIMEDATE \*FileCreated,  

      TIMEDATE far \*FileModified**);**



**Description :**



This
function returns information regarding one of the attachments of the specified
mail message.  The attachment of interest is specified by an index from 0 to
the number of attachments - 1.  

  

The BLOCKID value obtained using this function refers to memory within a note. 
This memory is managed by Domino, and should not be freed by the application.  

  

If desired, include nsfdata.h to define ATTRIB\_xxx  and HOST\_xxx symbols.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

Num  -  Attachment number (0-n).  

  




Output :  

(routine)  -  FALSE if there are no attachments; otherwise TRUE.  

  

  

bhItem  -  Block ID of the attachment item.  

  

FileName  -  File name of the attachment (null-terminated), up to
MAXPATH+1(includes null terminator).  Optional - specify NULL if not to be returned.  

  

FileSize  -  File size in bytes.  Optional - specify NULL if not to be
returned.  

  

FileAttributes  -  File attributes:  ATTRIB\_READONLY, ATTRIB\_PRIVATE.  Optional
- specify NULL if not to be returned.  

  

FileHostType  -  File host type:  HOST\_MSDOS, HOST\_MAC, HOST\_UNKNOWN.  Optional
- specify NULL if not to be returned.  

  

FileCreated  -  File creation time.  Optional - specify NULL if not to be
returned.  

  

FileModified  -  File modification time.  Optional - specify NULL if not to be
returned.  

  




 **Sample Usage :**


    for (Att = 0;
MailGetMessageAttachmentInfo(hMessage, Att,   

                            &bhAttachment, OriginalFileName,   

                            NULL, NULL, NULL, NULL, NULL); Att++)  

    {  

        printf("\tAttachment %d = '%s'\n", Att, OriginalFileName);  

    }


 **See Also :**


**[MailExtractMessageAttachment](MailExtractMessageAttachment.md)**



----------------------------------------------------------------------------------------------------------


 





