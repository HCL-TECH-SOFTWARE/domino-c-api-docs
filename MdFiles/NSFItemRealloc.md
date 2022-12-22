




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



**NSFItemRealloc** **-
Reallocate memory associated with an item value.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemRealloc(**  

      BLOCKID  item\_blockid,  

      BLOCKID far \*value\_blockid\_ptr,  

      DWORD  value\_len**);**



**Description :**



This
function reallocates the memory block associated with an item's value to the
amount requested. Use this function to change the amount of memory associated
with an item's value. If possible, this function resizes the memory block that
contains the value, otherwise the function allocates a new block and copies the
existing value there, and deletes the old block. Since the memory block might
move, you should unlock it if necesssary (using OSUnlockBlock) before calling
this function.  

  

This function stores the new value length in the item header and returns the
BLOCKID of the new block of memory.  The new block will contain the existing
value of the item, up to the length of the block.  On successful return,  the
caller should immediately write the new item value to the memory identified by
the returned BLOCKID.  

  

If this function returns successfully and a subsequent error prevents you from
writing the new item value to the new memory area, either delete the item from
the note or do not update the note to disk. Otherwise the value will not have a
consistent length, and Domino or Notes may detect the item as damaged.


 


**Parameters :**



Input :  

item\_blockid  -  BLOCKID of Item whose size you wish to change.  

  

value\_blockid\_ptr  -  A pointer to the value's BLOCKID.  The reallocation will
maintain the current contents of the item's value.   

  

value\_len  -  A DWORD containing the new length of the Item's value required. 
This length must include the  data type word.  If it does not, subsequent
manipulation of the value's BLOCKID will overwrite other areas of memory.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - upon successfully copying the item.  

  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

value\_blockid\_ptr  -   If the resizing requires any change in location within
memory managed by Domino and Notes,  the value's BLOCKID will be modified
accordingly and returned.  

  




 **Sample Usage :**


    // get the field  

  

    if ( err = NSFItemInfo(hNote,  

                     szItemName,  

                     lstrlen(szItemName),  

                     &item\_block,  

                     &item\_type,  

                     &value\_block,  

                     &value\_len))  

       goto done;  

  

    wsprintf(szBuff, "Got item %s, type 0x%04x, len 0x%08lx",
szItemName, item\_type,                          

                         value\_len);  

  

  

    // Realloc to a slightly shorter length  

  

    newlen = value\_len - 200;  

  

    if ( (old\_rt\_field = OSLockBlock(char, value\_block)) == NULL)  

      {  

        goto done;  

      }   

      

    /\* Allocate a buffer to hold the new data. \*/  

    new\_rt\_field = malloc((WORD) newlen + sizeof(WORD));  

  

    // Copy the new value to memory   

    memcpy(new\_rt\_field, old\_rt\_field, (WORD) newlen);  

  

    OSUnlockBlock(value\_block);  

  

    if (err = NSFItemRealloc(item\_block, &value\_block, newlen))  

      goto done;  

  

    wsprintf(szBuff, "Reallocated to length 0x%08lx", newlen);  

      

    new\_block\_ptr = OSLockBlock(char, value\_block);  

    if (new\_block\_ptr == NULL)  

      {  

        goto done;  

      }   

  

    memcpy(new\_block\_ptr, new\_rt\_field, (WORD) newlen);  

      

    OSUnlockBlock(value\_block);  

    NSFNoteUpdate(hNote, 0);  

      

    free(new\_rt\_field);  

    


 **See Also :**


**[NSFItemScan](NSFItemScan.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemQuery](NSFItemQuery.md)**



----------------------------------------------------------------------------------------------------------


 





