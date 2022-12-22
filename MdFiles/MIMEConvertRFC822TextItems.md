




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



**MIMEConvertRFC822TextItems** **- Convert
all TYPE\_RFC822\_TEXT items into their pre-V5 equivalents.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEConvertRFC822TextItems(**  

      NOTEHANDLE  hNote,  

      BOOL  bCanonical**);**



**Description :**



This
function converts the all TYPE\_RFC822\_TEXT items in an open note to their
pre-V5 equivalents; i.e., to TYPE\_TEXT, TYPE\_TEXT\_LIST, or TYPE\_TIME.    It
does not update the Domino database; to update the database, call
NSFNoteUpdate.


 


You must
specify as input the handle to the open note and a BOOLEAN value indicating if
the note was opened in canonical format (TRUE) or host format (FALSE).


 


MIMEConvertRFC822TextItems
converts all TYPE\_RFC822\_TEXT items to the appropriate pre-V5 item types.  For
example, MIMEConvertRFC822TextItems converts the PostedDate TYPE\_RFC822\_TEXT
item to a TYPE\_TIME item.  (PostedDate is the Notes equivalent of the 'Date:'
header in Internet format messages; see also the discussion of the
MIMEHeaderNameToItemName and MIMEItemNameToHeaderName APIs below for
information on mapping between Notes item names and Internet message header
names.)


 


 


**Parameters :**



Input :  

hNote  -  The handle to the open note containing the item to be converted.  

  

bCanonical  -  bCanonical  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the item.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


WORD wNoteFlags;


BOOL bCanonical;


STATUS error;


 


NSFNoteGetInfo(hNote,
\_NOTE\_FLAGS, &wNoteFlags);


 


bCanonical =
(wNoteFlags & NOTE\_FLAG\_CANONICAL) != 0;


 


if (error =
MIMEConvertRFC822TextItems(hNote, bCanonical)) {


        goto exit;


}


 


 




----------------------------------------------------------------------------------------------------------


 





