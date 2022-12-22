




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




**Initial Release 4.51**



**Function : Views; Folders**



**NIFLocateNote** **- Update
collection position for a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFLocateNote(**  

      HCOLLECTION  hCollection,  

      COLLECTIONPOSITION far \*IndexPos,  

      NOTEID  NoteID**);**



**Description :**



When a
collection is modified (for example, when another user adds or deletes a
document), the collection position for a note may no longer be valid. 
NIFLocateNote will locate the specified note ID in the collection, and update
the collection position to the new position.


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection.  

  

IndexPos  -  Pointer to the old collection position.  

  

NoteID  -  Note ID of the note to locate.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_NOT\_FOUND  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

IndexPos  -  Collection position updated to match the position in the modified
collection.  

  




 **See Also :**


**[NIFUpdateCollection](NIFUpdateCollection.md)**



----------------------------------------------------------------------------------------------------------


 





