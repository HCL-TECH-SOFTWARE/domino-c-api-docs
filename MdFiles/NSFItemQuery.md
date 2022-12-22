




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




 


**Function : Item (Field)**



**NSFItemQuery** **- Given
BLOCKID of item, get all item and value info.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



void
LNPUBLIC **NSFItemQuery(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  item\_bid,  

      char far \*item\_name,  

      WORD  return\_buf\_len,  

      WORD far \*name\_len\_ptr,  

      WORD far \*item\_flags\_ptr,  

      WORD far \*value\_datatype\_ptr,  

      BLOCKID far \*value\_bid\_ptr,  

      DWORD far \*value\_len\_ptr**);**



**Description :**



This
function takes a handle to an open note, the BLOCKID of any item in that note,
and the length of the text buffer that is to receive the item name.  It returns
all of the information that is typically required when appending an item using
NSFItemAppendByBLOCKID: name, name length, flags, value data type, a BLOCKID
associated with the value, and value length.  This function and NSFItemQueryEx
are the only direct means of obtaining item flags.  The function NSFItemScan
provides a callback routine which can also be used to obtain the contents of
the item flags.  

  

The BLOCKID values obtained using this function refer to memory within a note. 
This memory is managed by Domino and Notes, and should not be freed by the
application.


 


**Parameters :**



Input :  

note\_handle  -  A handle to the open note you want to look in.  

  

item\_bid  -  The BLOCKID of a item in the note obtained from a call to 
NSFItemInfo or NSFItemInfoNext.  

  

return\_buf\_len  -  A Word containing the length of the text buffer.  

  




Output :  

item\_name  -  Address of the text buffer in which the item name is returned.  

  

name\_len\_ptr  -  Address of the WORD in which the actual length of item\_name is
returned.  

  

item\_flags\_ptr  -  Address of the WORD in which the value of the item flags is
returned.    

  

value\_datatype\_ptr  -  Address of the WORD in which the value data type is
returned.  

  

value\_bid\_ptr  -  Address of the BLOCKID in which the item value BLOCKID is
returned.  Lock this BLOCKID by calling OSLockBlock. The resulting pointer
always points to the datatype WORD, followed by the actual value. The data type
word is always in Host format.  The value following the data type  word is in
Domino Canonical format unless the data type is one of TYPE\_TEXT, 
TYPE\_TEXT\_LIST,   TYPE\_USERID, TYPE\_NUMBER, TYPE\_NUMBER\_RANGE,  

TYPE\_HIGHLIGHTS, TYPE\_NOTEREF\_LIST, TYPE\_NOTELINK\_LIST, TYPE\_ERROR, or
TYPE\_UNAVAILABLE  

  

value\_len\_ptr  -  Address of the DWORD in which the length of the item value is
returned.  This length includes the Domino data type WORD that is prefixed to
the actual data.  

  




 **Sample Usage :**


/\* Find Item in Note1
and print the ITEM\_FLAGS \*/  

  

   if ( error\_status = NSFItemInfo(note1\_handle, TEXT\_ITEM,  

                           strlen(TEXT\_ITEM), &item\_bid,  

                           NULL, NULL, NULL))  

       goto Exit;  

  

   NSFItemQuery(note1\_handle, item\_bid,  

                item\_name\_buf, name\_buf\_len,  

                &item\_name\_len, &item\_flags, &value\_type,  

                &value\_bid, &value\_len);  

  

   item\_name\_buf[item\_name\_len] = '\0';  

  

   printf("Item %s has the following Item Flags set:\n",  

          item\_name\_buf);  

  

   if (item\_flags & ITEM\_SIGN)  

       printf("\tITEM\_SIGN\n");  

   if (item\_flags & ITEM\_SEAL)  

       printf("\tITEM\_SEAL\n");  

   if (item\_flags & ITEM\_SUMMARY)  

       printf("\tITEM\_SUMMARY\n");  

   if (item\_flags & ITEM\_PROTECTED)  

       printf("\tITEM\_PROTECTED\n");


 **See Also :**


**[NSFItemAppendByBLOCKID](NSFItemAppendByBLOCKID.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemQueryEx](NSFItemQueryEx.md)**


**[NSFItemScan](NSFItemScan.md)**



----------------------------------------------------------------------------------------------------------


 





