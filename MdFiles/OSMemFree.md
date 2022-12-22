




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




 


**Function : OS Memory**



**OSMemFree** **-
Deallocate (free) a block of Domino memory.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemFree(**  

      DHANDLE  Handle**);**



**Description :**



OSMemFree is
used to deallocate a block of Domino memory that was created via OSMemAlloc. 
In order for the deallocation to take place, the lock reference count for the
memory block must be zero. In other words, all OSLockObject operations made to
the memory block must be matched with an OSUnlockObject operation before memory
can be freed.  

  

Calling this routine with a HANDLE that is invalid or out of range, or with a
HANDLE for a memory object that is still locked, will result in a Notes PANIC
halt .  

  

Note: this routine must be called to free the memory objects specifically
created by you with OSMemAlloc or returned by one of several functions.  Each
function description will mention any specific objects you must 'free'.   The
following discussion will organize C API functions into several categories,
based on the way they handle the memory they create, manage, and destroy.  

  

Generally, functions that create database objects come in pairs, which could be
regarded as symmetrical functions.  A pair such as NSFNoteOpen and NSFNoteClose
are a case in point; any memory objects created by NSFNoteOpen will be freed by
NSFNoteClose.  Also, since notes are composed of a header structure and a
variable number of memory objects called 'items' (fields), NSFNoteClose will
take care of freeing the memory associated with any items in a note.  You must
NOT free memory that is still associated with a note's "items" with
OSMemFree, as a subsequent NSFNoteClose will try to free the memory objects
that no longer exist and a Notes PANIC halt will be the result.  

  

Another category of functions transfers responsibility for existing memory
objects to symmetrical functions.  A function such as NSFItemAppendByBLOCKID
actually creates an association between an object in memory and a note.   You
must NOT free the memory associated with note "items" by NSFItemAppendByBLOCKID
with OSMemFree, as NSFNoteClose will try to do the same when it is called and a
Notes PANIC halt will be the result.  

  

Another category of functions absolves symmetrical functions of their
responsibility for existing memory objects.  Functions such as
NSFItemDeleteByBLOCKID or NSFItemDelete remove the association between an
object in memory (item) and a note, and  then perform an OSMemFree themselves.  

  

Another category of functions create memory objects for you, in order to return
information to the caller.  Generally, the size of these memory objects cannot
be forseen or efficiently limited.  These include, but are not limited to:
NIFReadEntries, NSFConvertItemToComposite, and NSFConvertItemToText.  Again,
the function descriptions will flag any arguments that create memory your
program is ultimately responsible for cleaning up.  

  

The final category of functions copy existing memory objects, transferring
responsibility for management of the object to a symmetrical function. 
NSFItemAppend actually copies a memory object and appends it as a note item
(field).  NSFNoteClose takes care of the copied data, and you are left with the
original object, which your program may either re-use or free.


 


**Parameters :**



Input :  

Handle  -  Handle for the memory object to be freed.  

  




Output :  

(routine)  -  Always returns NOERROR.  There is no need to check the return
value.  

  

  




 **Sample Usage :**


  

   if (wCleanUp & FREE\_HCDBUF)  

       OSMemFree(hCDBuf);  

  




 **See Also :**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemRealloc](OSMemRealloc.md)**


**[OSMemGetSize](OSMemGetSize.md)**


**[OSLockObject](OSLockObject.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 





