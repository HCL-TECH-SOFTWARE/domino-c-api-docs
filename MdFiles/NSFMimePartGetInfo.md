




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



**NSFMimePartGetInfo** **- get
information about a named MIME part item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartGetInfo(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      WORD \*pwPartType,  

      DWORD \*pdwFlags,  

      WORD \*pwReserved,  

      WORD \*pwPartLen,  

      BLOCKID \*pbhItem**);**



**Description :**



The function
NSFMimePartGetInfo returns information about a named TYPE\_MIME\_PART item in an
open note.  The returned BLOCKID, bhItem, is the BLOCKID for the first item of
name 'pchItemName' found by NSFMimePartGetInfo.


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

pchItemName  -  Pointer to buffer containing item name to use; typically should
be MAIL\_BODY\_ITEM.  

  

wItemNameLen  -   item name length.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully fetched the MIME part info.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

pwPartType  -  pointer to location for the returned MIME part type.  

  

pdwFlags  -  pointer to location for the returned MIME part flags.  

  

pwReserved  -  reserved -- presently unused.  

  

pwPartLen  -  pointer to location for returned part data length in bytes.  

  

pbhItem  -  pointer to location for returned BLOCKID for MIME part item.  

  




 **Sample Usage :**


    STATUS error;


WORD wPartType;


DWORD dwFlags;


WORD wReserved;


WORD wPartLen;


BLOCKID bhItem;


 


if (error =
NSFMimePartGetInfo(hNote,


                                       MAIL\_BODY\_ITEM,


                                       sizeof(MAIL\_BODY\_ITEM)-1,


                                       &wPartType,


                                       &dwFlags,


                                       &wReserved,


                                       &wPartLen,


                                       &bhItem))
{


        goto exit;


}


 


 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[NSFMimePartGetInfoByBLOCKID](NSFMimePartGetInfoByBLOCKID.md)**


**[NSFMimePartGetInfoNext](NSFMimePartGetInfoNext.md)**



----------------------------------------------------------------------------------------------------------


 





