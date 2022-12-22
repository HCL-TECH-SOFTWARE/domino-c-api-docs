




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



**Function : Mail; MIME**



**NSFMimePartGetInfoByBLOCKID** **- given its
BLOCKID, get information about a MIME part item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartGetInfoByBLOCKID(**  

      BLOCKID  bhItem,  

      WORD \*pwPartType,  

      DWORD \*pdwFlags,  

      WORD \*pwReserved,  

      WORD \*pwPartOffset,  

      WORD \*pwPartLen,  

      WORD \*pwBoundaryOffset,  

      WORD \*pwBoundaryLen,  

      WORD \*pwHeadersOffset,  

      WORD \*pwHeadersLen,  

      WORD \*pwBodyOffset,  

      WORD \*pwBodyLen**);**



**Description :**



The function
NSFMimePartGetInfoByBLOCKID returns information about a TYPE\_MIME\_PART item in
an open note, given its BLOCKID.  If wBoundaryLen or wHeadersLen are returned
as 0, there is no boundary or headers, respectively, for the TYPE\_MIME\_PART
item.


 


 


**Parameters :**



Input :  

bhItem  -  the BLOCKID for the TYPE\_MIME\_PART item.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully fetched the MIME part info.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

pwPartType  -  pointer to location for the returned MIME part type.  

  

pdwFlags  -  pointer to location for the returned MIME part flags.  

  

pwReserved  -  reserved -- presently unused.  

  

pwPartOffset  -  offset of the MIME part data within the TYPE\_MIME\_PART item;
i.e., after the MIME\_PART ODS structure.  

  

pwPartLen  -  pointer to location for returned part data length in bytes.  

  

pwBoundaryOffset  -  offset of the part boundary, if any, within the TYPE\_MIME\_PART
item; i.e., after the MIME\_PART ODS structure.  

  

pwBoundaryLen  -  length of the boundary.  

  

pwHeadersOffset  -  offset of the part headers, if any, within the
TYPE\_MIME\_PART item; i.e., after the MIME\_PART ODS structure.  

  

pwHeadersLen  -  length of the headers.  

  

pwBodyOffset  -  offset of the part body within the TYPE\_MIME\_PART item; i.e.,
after the MIME\_PART ODS structure.  

  

pwBodyLen  -  length of the body.  

  




 **Sample Usage :**


    STATUS error;


BLOCKID bhValue;


DWORD dwValueLen;


BLOCKID bhItem;


WORD wPartType;


DWORD dwFlags;


WORD wReserved;


WORD wPartOffset;


WORD wPartLen;


WORD wBoundaryOffset;


WORD wBoundaryLen;


WORD wHeadersOffset;


WORD wHeadersLen;


WORD wBodyOffset;


WORD wBodyLen;


 


if (error =
NSFItemInfo(hNote,


                              MAIL\_BODY\_ITEM,


                              sizeof(MAIL\_BODY\_ITEM)-1,


                              &bhItem,


                              NULL,


                              &bhValue,


                              &dwValueLen))
{


        goto exit;


}


 


if (error =
NSFMimePartGetInfoByBLOCKID(bhItem,


                                                
&wPartType,


                                                
&dwFlags,


                                                
&wReserved,


                                                
&wPartOffset,


                                                
&wPartLen,


                                                
&wBoundaryOffset,


                                                
&wBoundaryLen,


                                                
&wHeadersOffset,


                                                
&wHeadersLen,


                                                
&wBodyOffset,


                                                
&wBodyLen)) {


        goto exit;


}


 


 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NSFMimePartGetInfo](NSFMimePartGetInfo.md)**


**[NSFMimePartGetInfoNext](NSFMimePartGetInfoNext.md)**



----------------------------------------------------------------------------------------------------------


 





