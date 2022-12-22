




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



**MIMEConvertRFC822TextItemByBLOCKID** **- Convert a
TYPE\_RFC822\_TEXT item into it's pre-V5 equivalent.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEConvertRFC822TextItemByBLOCKID(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhItem,  

      BLOCKID  bhValue**);**



**Description :**



This
function converts the input TYPE\_RFC822\_TEXT item in an open note to its pre-V5
equivalent; i.e. to TYPE\_TEXT, TYPE\_TEXT\_LIST, or TYPE\_TIME.    It does not
update the Domino database; to update the database, call NSFNoteUpdate.


 


You must
specify as input the handle to the open note, a BLOCKID for the item, and a
BLOCKID for the item value.


 


MIMEConvertRFC822TextItem
converts the named input item to the appropriate pre-V5 item type.  For
example, MIMEConvertRFC822TextItem converts the PostedDate TYPE\_RFC822\_TEXT
item to a TYPE\_TIME item.  (PostedDate is the Notes equivalent of the 'Date:'
header in Internet format messages; see also the discussion of the
MIMEHeaderNameToItemName and MIMEItemNameToHeaderName APIs below for information
on mapping between Notes item names and Internet message header names.)


 


 


**Parameters :**



Input :  

hNote  -  The handle to the open note containing the item to be converted.  

  

bhItem  -  BLOCKID for the item.  

  

bhValue  -  BLOCKID for the item value.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the item.  

     ERR\_MISC\_INVALID\_ARGS - Item is not a TYPE\_RFC822\_TEXT item.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


BLOCKID bhItem;


BLOCKID bhValue;


WORD wDataType;


DWORD dwValueLen;


STATUS error;


 


if (error =
NSFItemInfo(hNote,


                              MAIL\_POSTEDDATE\_ITEM,
sizeof(MAIL\_POSTEDDATE\_ITEM)-1,


                              &bhItem,
&wDataType, &bhValue, &dwValueLen)) {


        goto exit;


}


 


if (error =
MIMEConvertRFC822TextItemByBLOCKID(hNote, bhItem, bhValue)) {


        goto exit;


}


 


 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





