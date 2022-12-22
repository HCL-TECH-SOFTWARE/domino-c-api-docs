




<!--
 /\* Font Definitions \*/
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



**NSFMimePartGetPart** **- returns
the MIME\_PART ODS structure for a given TYPE\_MIME\_PART item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartGetPart(**  

      BLOCKID  bhItem,  

      DHANDLE \*phPart**);**



**Description :**



The function
NSFMimePartGetPart returns the MIME\_PART ODS structure for a TYPE\_MIME\_PART
item, given its BLOCKID.  The caller is responsible for freeing the block of
memory in which the MIME\_PART is returned.


 


**Parameters :**



Input :  

bhItem  -  the BLOCKID for the TYPE\_MIME\_PART item.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully added the MIME part.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

phPart  -  pointer to location for the handle to the allocated memory
containing the MIME\_PART.  

  




 **Sample Usage :**


STATUS error;  

BLOCKID bhValue;  

DWORD dwValueLen;  

BLOCKID bhItem;  

DHANDLE hPart;  

MIME\_PART \*pPart;  

  

if (error = NSFItemInfo(hNote,  

                                                     MAIL\_BODY\_ITEM,  

                                                     sizeof(MAIL\_BODY\_ITEM)-1,  

                                                     &bhItem,  

                                                     NULL,  

                                                     &bhValue,  

                                                     &dwValueLen)) {  

        goto exit;  

}  

  

if (error = NSFMimePartGetPart(bhItem, &hPart)) {  

        goto exit;  

}  

  

pPart = OSLock(MIME\_PART, hPart);  

  

/\* perform ODS operations... \*/  

  

OSUnlockAndFree(hPart);  

  




 **See Also :**


**[BLOCKID](BLOCKID.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFMimePartGetInfo](NSFMimePartGetInfo.md)**


**[NSFMimePartGetInfoByBLOCKID](NSFMimePartGetInfoByBLOCKID.md)**


**[NSFMimePartGetInfoNext](NSFMimePartGetInfoNext.md)**



----------------------------------------------------------------------------------------------------------


 





