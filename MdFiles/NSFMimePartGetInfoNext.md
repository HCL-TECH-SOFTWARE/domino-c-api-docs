




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



**NSFMimePartGetInfoNext** **- get
information about a subsequent named MIME part item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartGetInfoNext(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhItem,  

      char \*pchItemName,  

      WORD  wItemNameLen,  

      WORD \*pwPartTyp,  

      DWORD \*pdwFlags,  

      WORD \*pwReserved,  

      WORD \*pwPartLen,  

      BLOCKID \*pbhItemNext**);**



**Description :**



The function
NSFMimePartGetInfoNext returns information about a subsequent named
TYPE\_MIME\_PART item in an open note, using the BLOCKID returned by NSFMimePartGetInfo
for the first named TYPE\_MIME\_PART item.  The returned BLOCKID, bhItemNext, is
the BLOCKID for the just fetched item of name 'pchItemName', to be passed as
bhItem on subsequent calls to NSFMimePartGetInfoNext.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

bhItem  -  BLOCKID for the current TYPE\_MIME\_PART of the given name.  

  

pchItemName  -  Pointer to buffer containing item name to use; typically should
be MAIL\_BODY\_ITEM.  

  

wItemNameLen  -  item name length.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully fetched the MIME part info.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

pwPartTyp  -  pointer to location for the returned MIME part type.  

  

pdwFlags  -  pointer to location for the returned MIME part flags.  

  

pwReserved  -  reserved -- presently unused.  

  

pwPartLen  -  pointer to location for returned part data length in bytes.  

  

pbhItemNext  -  pointer to location for returned BLOCKID for next MIME part
item.  

  




 **Sample Usage :**


STATUS error;


WORD wPartType;


DWORD dwFlags;


WORD wReserved;


WORD wPartLen;


BLOCKID bhItem;


BLOCKID bhItemNext;


int n = 0;


 


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


 


while
(!ISNULLBLOCKID(bhItem)) {


        ++n;


 


        if (error =
NSFMimePartGetInfoNext(hNote,


                                                 
bhItem,


                                                 
MAIL\_BODY\_ITEM,


                                                 
sizeof(MAIL\_BODY\_ITEM)-1,


                                                 
&wPartType,


                                                 
&dwFlags,


                                                 
&wReserved,


                                                 
&wPartLen,


                                                 
&bhItemNext)) {


               goto
exit;


        }


 


        bhItem =
bhItemNext;


}


 


 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[NSFMimePartGetInfo](NSFMimePartGetInfo.md)**


**[NSFMimePartGetInfoByBLOCKID](NSFMimePartGetInfoByBLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 





