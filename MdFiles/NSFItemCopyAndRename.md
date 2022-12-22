




<!--
 /\* Font Definitions \*/
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




 


**Function : Database; Item (Field);
Item (Field) Information**



**NSFItemCopyAndRename** **- Copy an
item from one note to another note and rename it.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS **NSFItemCopyAndRename(**  

      DHANDLE  hnote,  

      BLOCKID  bhItem,  

      const char \*pszNewItemName**);**



**Description :**



Copy a
single item from one note to the end of another note. Optionally rename the
item in the target note.


 


**Parameters :**



Input :  

hnote  -  It is an open Note handle.  

  

bhItem  -  The block id of the note item to be copied.  

  

pszNewItemName  -  An optional new name for the destination item.  If NULL,
name is copied with original item.  

  




Output :  

(routine)  -  Return status from the call either success or an error.   

              NOERROR, on success.  

  

  




 **Sample Usage :**


      /\*
Presumes hSrcNote and hDstNote are both opened NOTEHANDLES prior to calling. \*/


 


            void
far PASCAL CopyItem(NOTEHANDLE hSrcNote,char \*pSrcItem, NOTEHANDLE
hDstNote,char \*pDstItem)


            {


                        BLOCKID
bhItem;


                        char
\*pEffectiveDstItem = (pDstItem ? pDstItem : pSrcItem);


                        char
szDstItem[MAXINTF]; 


 


                        //
To deal with both responses and the parent, shortcut a copy to self. 


                        //



                        if
(hSrcNote == hDstNote) 


                                    return;



 


                        NSFItemDelete(hDstNote,
szDstItem, Cstrlen(szDstItem));


            


                        if
(NOERROR == NSFItemInfo(hSrcNote, pSrcItem, Cstrlen(pSrcItem), &bhItem,
NULL, NULL, NULL)) 


                        {


                                    BLOCKID
bhNewItem; 


 


                                    NSFItemCopyAndRename(hDstNote,
bhItem, szDstItem);


 


                                    if
(NOERROR == NSFItemInfo(hDstNote, szDstItem, Cstrlen(szDstItem),
&bhNewItem, NULL, NULL, NULL))


                                    {


                                                NOTE\_ITEM
\*item = OSLockBlock(NOTE\_ITEM,bhNewItem);


                                                item->ItemFlags
|= ITEM\_SUMMARY; 


                                                OSUnlockBlock(bhNewItem);



                                    }


                        }


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





