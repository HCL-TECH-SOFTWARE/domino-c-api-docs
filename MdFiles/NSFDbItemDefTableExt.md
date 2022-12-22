




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




**Initial Release 5.0**



**Function : Database**



**NSFDbItemDefTableExt** **- Get the
extended version of the database's Item Definition Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbItemDefTableExt(**  

      DBHANDLE  hDB,  

      ITEMDEFTABLEEXTHANDLE far \*retItemNameTable**);**



**Description :**



The extended
version of the Item Definition Table for a database contains the number of
items, name and type of all the items defined in that database.  Examples are
field names, form names, design names, and formula labels.  Applications can
obtain a copy of the extended version of the Item Definition Table by calling
NSFDbItemDefTableExt, which returns a memory handle for the copy of the table. 
The application can then call the following functions to lock, extract, unlock,
and free information from the table:


 


       
NSFItemDefExtLock, NSFItemDefExtEntries, NSFItemExtGetEntry,
NSFItemDefExtUnlock, NSFItemDefExtFree.


  

For details on the structure of the extended version of the Item Definition
Table, please see the descriptions for ITEM\_DEFINITION\_TABLE\_EXT,  ITEM\_DEFINITION\_EXT,
and ITEM\_DEFINITION\_TABLE\_LOCK.


 


 


**Parameters :**



Input :  

hDB  -  A handle to the Domino database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Operation succeeded.  

  

  

  

retItemNameTable  -  The address of an ITEMDEFTABLEEXTHANDLE where the handle
for the extended version of the Item Definition Table of a database is
returned.  

  




 **Sample Usage :**



    /\*
Local data declarations \*/


    


    /\*
database handle \*/


   
DBHANDLE                                    db\_handle;


   
ITEMDEFTABLEEXTHANDLE                       hItemDefExt;


   
ITEM\_DEFINITION\_TABLE\_EXT                   \*pItemDefExt;


   
ITEM\_DEFINITION\_TABLE\_LOCK                  ExtLock;


   
DWORD                                       i, NumEntries;


   
WORD                                        ItemType, ItemLength;


   
char                                        \*pItemName;


    char                                       
ItemName[128];


   
char                                        NewItemName[128];


   
char                                        \*db\_name;


   
char                                        szDBName[MAXPATH];


    STATUS                                     
error=0;


 


    db\_name
= szDBName;


    


    /\* Open
the database. \*/


    


    if
(error = NSFDbOpen (db\_name, &db\_handle))


        goto
Exit0;


    


    /\* Get
a handle to the ITEM\_DEFINITION\_TABLE\_EXT structure \*/


    


    if
(error = NSFDbItemDefTableExt (db\_handle, &hItemDefExt))


        goto
Exit1;


 


    /\* lock
the ITEM\_DEFINTION\_TABLE\_EXT structure and get a pointer \*/


 


   
pItemDefExt = OSLock(ITEM\_DEFINITION\_TABLE\_EXT, hItemDefExt);


 


    /\* Lock
the contents of the ITEM\_DEFINITION\_EXT structure \*/


    


    if
(error = NSFItemDefExtLock(pItemDefExt, &ExtLock))


        goto
Exit2;


 


    /\* Get
the number of item entries from the structure \*/


    


    if
(error = NSFItemDefExtEntries(&ExtLock, &NumEntries))


        goto
Exit3;


 


   
printf("NumEntries:%d\n\n",NumEntries);


    


   
pItemName = &ItemName[0];


 


    /\* for
each item... \*/


    for
(i=0; i<NumEntries; i++)


    {


 


      /\*
get the item's type, length, and name \*/


      if
(error = NSFItemDefExtGetEntry(&ExtLock, i, &ItemType, &ItemLength,
&pItemName))


         
goto Exit3;


 


      /\*
copy character stream up to Item Length \*/


     
memcpy(&NewItemName[0],pItemName,ItemLength);


          


      /\*
null terminate the character stream \*/


     
NewItemName[ItemLength]='\0';


      


     
printf("Item %d\n", i);


     
printf("ItemType:%d\n", ItemType);


     
printf("ItemLength:%d\n", ItemLength);


     
printf("ItemName:%s\n\n", NewItemName);


    }


 


Exit3:


 


    /\*
Unlock the ITEM\_DEFINITION\_EXT structure within the ITEM\_DEFINITION\_TABLE\_EXT


      
structure \*/


    


    if
(!error)


      error
= NSFItemDefExtUnlock(pItemDefExt, &ExtLock);


 


Exit2:


 


    /\* Free
the contents of the ITEM\_DEFINITION\_EXT structure within the 


      
ITEM\_DEFINITION\_TABLE\_EXT \*/


    if
(!error)


      error
= NSFItemDefExtFree(pItemDefExt);


 


    /\*
unlock and free the handle to the ITEM\_DEFINITION\_TABLE\_EXT structure \*/


   
OSUnlock(hItemDefExt);


   
OSMemFree(hItemDefExt);


 


 


 


Exit1:


    /\*
Close the database. \*/


    


   
NSFDbClose (db\_handle);


 


Exit0:


 


   
return(ERR(error));


 


}


 


 **See Also :**


**[ITEM\_DEFINITION\_EXT](ITEM_DEFINITION_EXT.md)**


**[ITEM\_DEFINITION\_TABLE\_EXT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D230ED443AC3962085256711004ED105)**


**[ITEM\_DEFINITION\_TABLE\_LOCK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/901659ECD32C4D5185256711004FD3A8)**


**[NSFItemDefExtEntries](NSFItemDefExtEntries.md)**


**[NSFItemDefExtFree](NSFItemDefExtFree.md)**


**[NSFItemDefExtGetEntry](NSFItemDefExtGetEntry.md)**


**[NSFItemDefExtLock](NSFItemDefExtLock.md)**


**[NSFItemDefExtUnlock](NSFItemDefExtUnlock.md)**



----------------------------------------------------------------------------------------------------------


 





