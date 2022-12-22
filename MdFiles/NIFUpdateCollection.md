




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




 


**Function : Views; Folders**



**NIFUpdateCollection** **- Update a
collection.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFUpdateCollection(**  

      HCOLLECTION  hCollection**);**



**Description :**



This
function updates an open collection.  If the collection is out of date with
respect to a database (if it was updated recently via NSFNoteUpdate), this
routine can be called to perform a partial search of the database for all notes
modified since the last time the collection was updated, and all notes found in
the search are then added to the collection.  You should update a collection
when you have finished adding and/or deleting documents that you might
subsequently wish to recognize in that collection.  

  

A collection may not be automatically updated when it is closed and then
reopened. This will happen when concurrent applications are modifying databases
in which the views and documents are in separate databases.


 


When a
collection is updated, the positions of documents in the collection may
change.  Any collection positions that have been obtained may no longer be
correct.  The collection positions for these notes should be updated by calling
NIFLocateNote.


 


**Parameters :**



Input :  

hCollection  -  The handle of the collection you want to update.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is:  

  

NOERROR - Collection successfully updated .  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFCloseCollection](NIFCloseCollection.md)**


**[NIFLocateNote](NIFLocateNote.md)**



----------------------------------------------------------------------------------------------------------


 





