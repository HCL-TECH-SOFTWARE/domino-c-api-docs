




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




**Initial Release 7.0**



**Function : Database**



**NSFDbStampNotesMultiItem** **- Set same
item value for every note in ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbStampNotesMultiItem(**  

      DBHANDLE  hDB,  

      DHANDLE  hTable,  

      DHANDLE  hInNote**);**



**Description :**



This
function takes the  item values in the given note and stores (stamps) them in
all the notes specified by an ID Table.  It overwrites the current item values,
thereby updating the last modified time/date of each Note processed.  If the
item does not exist or is of a different data type, NSFDbStampNotesMultiItem()
will create/delete the item and append the new value as required.


 


If you do
not have the proper access to modify any one of the notes in the ID Table,
ERR\_NOACCESS will be returned.  Only those documents you are able to modify
have been stamped.


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  

hTable  -  A handle to an ID Table.  

  

hInNote  -  Handle of note containing specified item values to stamp to the set
of notes contained in the table.  

  




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

  

  




 **See Also :**


**[NSFDbGetModifiedNoteTable](NSFDbGetModifiedNoteTable.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**



----------------------------------------------------------------------------------------------------------


 





