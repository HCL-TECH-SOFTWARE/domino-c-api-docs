




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




 


**Symbolic Value : Views**



**OPEN\_xxx (collection)** **-** NIFOpenCollection()
- OpenFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      OPEN\_REBUILD\_INDEX      -  Throw away existing index and
rebuild it from scratch.  

  

      OPEN\_NOUPDATE   -  Do not update index or unread list as part of the
open.  

  

      OPEN\_DO\_NOT\_CREATE   -  If collection object has not yet been created, do
NOT create it automatically. Instead return a special internal error
ERR\_COLLECTION\_NOT\_CREATED.  

  

      OPEN\_SHARED\_VIEW\_NOTE         -  Tells NIF to "own" the view
note (which gets read while opening the collection) in memory, rather than the
caller "owning" the view note by default. If this flag is specified
on subsequent opens, and NIF currently owns a copy of the view note, it will
just pass back the view note handle rather than re-reading it from
disk/network. If specified, the the caller does NOT have to close the handle.
If not specified, the caller gets a separate copy, and has to NSFNoteClose the
handle when its done with it.  

  

      OPEN\_REOPEN\_COLLECTION        -  Force re-open of collection and thus,
re-read of view note. Also implicitly prevents sharing of collection handle,
and thus prevents any sharing of associated structures such as unread lists,
etc..  

  




**Description :**



These flags
control the manner in which NIFOpenCollection opens a collection of notes.


 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**



----------------------------------------------------------------------------------------------------------


 





