




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




 


**Function : Database**



**NSFDbStampNotes** **- Set same
item value for every note in ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbStampNotes(**  

      DBHANDLE  hDB,  

      DHANDLE  hTable,  

      const char far \*ItemName,  

      WORD  ItemNameLength,  

      void far \*Data,  

      WORD  DataLength**);**



**Description :**



This
function takes a given item value and stores it in all the notes specified by
an ID Table.  It overwrites the current item value, thereby updating the last
modified time/date of each Note processed.  If the item does not exist or is of
a different data type, NSFDbStampNotes() will create/delete the item and append
the new value as required.


 


If you do
not have the proper access to modify any one of the notes in the ID Table,
ERR\_NOACCESS will be returned.  Only those documents you are able to modify
have been stamped.


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  

hTable  -  A handle to an ID Table.  

  

ItemName  -  A pointer to a string containing the name of the Item you wish to
operate on.  This string does not have to be null-terminated.  

  

ItemNameLength  -  A WORD containing the length of the Item name.  

  

Data  -  A pointer to the value.  The first WORD of that storage must be the
Domino data type, followed by the data itself.  If the API program is running
on a non-Intel architecture system, and item type is one of TYPE\_COMPOSITE,
TYPE\_COLLATION, TYPE\_OBJECT, TYPE\_VIEW\_FORMAT, TYPE\_ICON, TYPE\_SIGNATURE,
TYPE\_SEAL, TYPE\_SEALDATA, TYPE\_SEAL\_LIST, TYPE\_WORKSHEET\_DATA or TYPE\_USERDATA,
then the data pointed to by Data must be in Domino canonical format.  

  

DataLength  -  A WORD containing the length of the data, including the leading
WORD of data type.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully stamped the notes contained in the ID Table.  

  

ERR\_DIRECTORY - This function is inappropriate for directories.  

  

ERR\_NO\_STAMPED\_NOTES - No documents were categorized(stamped).    

  

ERR\_NOACCESS - You are not authorized to modify one or more of the documents
specified.  Only those documents you are authorized to modify have been
stamped.  

  

ERR\_xxx - Errors returned by lower level Notes functions.  There are so many
possible causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


  

  

   /\* Please note that the first WORD of text\_item\_value was already \*/  

   /\* set to TYPE\_TEXT and text\_item\_size was adjusted accordingly.  \*/  

  

       case STAMP\_NOTES:  

            printf(" will be Stamped\n");  

            if (!(dataset\_state & HAVE\_CATEGORY))  

            {  

                printf("You must supply a category for action:
-C\n");  

                goto Exit;  

            }  

            if ( error\_status = NSFDbStampNotes(db\_handle\_src,  

                                 idtable\_handle, CATEGORIES\_ITEM\_NAME,  

                                 strlen(CATEGORIES\_ITEM\_NAME),  

                                 text\_item\_value,  

                                 text\_item\_size))  

                goto Exit;  

            break;  

  




 **See Also :**


**[NSFDbGetModifiedNoteTable](NSFDbGetModifiedNoteTable.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**



----------------------------------------------------------------------------------------------------------


 





