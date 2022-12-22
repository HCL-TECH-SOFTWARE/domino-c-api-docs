




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




 


**Function : Views; Folders**



**NIFReadEntries** **- Reads
information about entries in a collection.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFReadEntries(**  

      HCOLLECTION  hCollection,  

      COLLECTIONPOSITION far \*IndexPos,  

      WORD  SkipNavigator,  

      DWORD  SkipCount,  

      WORD  ReturnNavigator,  

      DWORD  ReturnCount,  

      DWORD  ReturnMask,  

      DHANDLE far \*rethBuffer,  

      WORD far \*retBufferLength,  

      DWORD far \*retNumEntriesSkipped,  

      DWORD far \*retNumEntriesReturned,  

      WORD far \*retSignalFlags**);**



**Description :**



This
function scans a collection and returns information about the entries in the
collection.  

  

The function takes as input a collection (parameter 1) and a starting location
in the collection (parameter 2). The function skips some number of entries
(possibly zero), based on parameters 3 and 4.  After skipping some entries, the
function begins reading the entries in the collection, based on parameters 5, 6
and 7. Parameters 5 and 6 specify how to navigate the collection while reading,
and parameter 7 specifies what information to return about each entry in the
collection.  

  

The information is returned in a buffer (parameter 8).  All the information
about the first entry appears first in the buffer, all the information about
the second entry appears next and so on. Within each entry, the information
occurs in the order of the bits in the bit flags READ\_MASK\_xxx.  

  

After a call to NIFReadEntries(), the collection position (parameter 2) points
to the last entry read. You can use repeated calls to NIFReadEntries to move
incrementally through a collection.  However, upon repeating the call to
NIFReadEntries(), use one of the NAVIGATE\_NEXT\_xxx skip navigate flags (the
third parameter) and use a skip count of 1L (the fourth parameter) to advance
the collection position past the last one read so that it begins reading with
the next entry in the collection.  

  

If the amount of information to be returned cannot fit in the return buffer,
then the SIGNAL\_MORE\_TO\_DO bit is set in the retSignalFlags parameter, no error
is returned, and the buffer is returned truncated on the last "whole"
entry that fits into the buffer.  There will never be a truncated entry in the
returned buffer. Therefore, you should always call NIFReadEntries in a loop and
test the SIGNAL\_MORE\_TO\_DO bit in the SignalFlags parameter. This ensures that
you obtain information about all the notes in a collection.    

  

After each call to NIFReadEntries is completed, you must check that the
returned buffer handle (8th argument) is not NULLHANDLE, and then call
OSLockObject to lock the buffer and obtain the address of the requested data. 
Also check the number of entries returned (11th argument) to ensure that the
buffer contains valid entries.  When you are through using the buffer, you must
call OSUnlockObject to unlock it and OSMemFree to deallocate it.    

  

Note: Even though the number of entries returned and/or the returned buffer
length are 0, you must use OSMemFree if the returned buffer handle is not
NULLHANDLE.  The return of a buffer handle that is not NULLHANDLE does not
necessarily mean that entries were found by NIFReadEntries.  Use the returned
number of entries to determine whether the buffer contains valid entries.


 


You can get
to the last N entries of a view by setting the Skip Navigator to NAVIGATE\_NEXT
| NAVIGATE\_CONTINUE, setting the SkipCount to MAXDWORD, setting the
ReturnNavigator to NAVIGATE\_PREV\_EXPANDED, and setting the ReturnCount to N (N
must be greater than 0).


 


For a very
quick way of getting the last entry of a view, set the Skip Navigator to
NAVIGATE\_NEXT | NAVIGATE\_CONTINUE, set the SkipCount to MAXDWORD, set the
ReturnNavigator to NAVIGATE\_CURRENT, set the retNumEntriesSkipped parameter to
NULL, and set the ReturnCount to N (N must be greater than 0).  For
optimization, do not use the full text seaarch navigator flags
(NAVIGATE\_xxx\_HIT) in the SkipNavigator.


 


**Parameters :**



Input :  

hCollection  -  The handle of the collection that you want to read.  

  

IndexPos  -  A pointer to a COLLECTIONPOSITION that holds the starting point
within the collection. The starting point controls which note in the collection
is the first note read. To start at the beginning of the collection, set
CollPosition.Level to 0 and CollPosition.Tumbler[0] to 1.  An alternative way
to start at the beginning of the collection is to set the CollPosition.Level to
0, set the CollPosition.Tumbler[0] to 0, set the skip navigate flag (third
parameter) to NAVIGATE\_NEXT and set the skip count (fourth parameter) to 1L.   

  

SkipNavigator  -  Flags that controls how the collection is navigated during
the "skip" operation. Skipping occurs before the collection is read
and may be used to pass over some of the collection's entries. The skip flags
are defined in NAVIGATE\_xxx.  

  

SkipCount  -  How many entries to skip before reading the collection. The skip
pattern is determined by SkipNavigator parameter. To skip no entries, set this
argument to 0.  

  

ReturnNavigator  -  Flags that control how the collection is navigated when the
entries are read (after skipping is complete). The read flags are defined in
NAVIGATE\_xxx. See the example below for how to read all the entries in a
collection.  

  

ReturnCount  -  The maximum number of entries that should be returned. To read all
the entries in the collection, set this argument to 0xFFFFFFFF. To stop reading
before the end of the collection, set this argument to the number of entries
you want.  

  

ReturnMask  -  Flags that control what information about the collection's
entries will be returned. The information flags are defined in READ\_MASK\_xxx,
and may be OR'ed together to combine functionailty.  If more than one flag is
requested, the order of the item's information in the buffer is the same order
as the flag's bit numbers (i.e. flag bit 0 precedes bit 1, then bit 2, etc).  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_UNSUPPORTED\_FLAGS  

ERR\_NONAMES  

  

  

IndexPos  -  A pointer to a COLLECTIONPOSITION indicating the last note in the
collection that was read by NIFReadEntries.  If the entire collection is not
read by a call to NIFReadEntries, this COLLECTIONPOSITION can be used as input
into the next call to NIFReadEntries.  In this case, be sure to set the skip
navigate flag and skip count so that the last note read in the previous call to
NIFReadEntries is skipped.  

  

rethBuffer  -  The address of a HANDLE variable in which the handle to a buffer
of information about this collection is returned.  This may be returned as
NULLHANDLE if there were no entries returned, so be sure to check for
NULLHANDLE before attempting to lock the returned handle.  

  

The caller is responsible for freeing this buffer using OSMemFree.  

  

retBufferLength  -  The address of a WORD in which the length of the
information buffer is returned. If you are not interested in this length, set
this argument to NULL.  

  

retNumEntriesSkipped  -  The address of a WORD in which the number of entries
that were skipped is returned. If you are not interested in this information,
set this argument to NULL.  

  

retNumEntriesReturned  -  The address of a DWORD in which the number of entries
is returned. If you are not interested in this information, set this argument
to NULL.  However, you should use this returned value to determine whether this
function found any entries.  

  

retSignalFlags  -  The address of a WORD in which various result flags are
returned.  If one of the the flags represented by SIGNAL\_ANY\_CONFLICT is set,
the collection has changed since it was last read. If the SIGNAL\_MORE\_TO\_DO
flag is set, then the end of the collection has not been reached and there
exists more information than could fit in the return buffer.  In this case,
NIFReadEntries should be called again to retrieve an additional buffer of
information.  The signal flags are defined in SIGNAL\_xxx, and are returned
OR'ed together.  

  




 **Sample Usage :**


/\* This code fragment
shows a typical call to NIFReadEntries. \*/  

  

/\* Set up the data structure, COLLECTIONPOSITION, that           \*/  

/\* controls where in the collection we will begin when we read  \*/  

/\* the collection.  Specify that we want to start at the beginning. \*/  

  

    CollPosition.Level = 0;  

    CollPosition.Tumbler[0] = 0;  

  

/\* Get a buffer of all the note IDs for the notes in this collection.  

Check the return code to see if the collection is empty. \*/  

  

do  

{  

    error = NIFReadEntries(  

               hCollection,           /\* handle to this collection \*/  

               &CollPosition,    /\* where to start in collection \*/  

               NAVIGATE\_NEXT,        /\* order to skip entries \*/  

               1L,                   /\* number to skip \*/  

               NAVIGATE\_NEXT,        /\* order to use after skipping \*/  

               0xFFFF,                /\* max return number \*/  

               READ\_MASK\_NOTEID,      /\* info we want \*/  

               &hBuffer,      /\* handle to info (return)        \*/  

               NULL,                  /\* length of buffer (return) \*/  

               NULL,                  /\* entries skipped (return) \*/  

               &NotesFound,           /\* number of notes (return) \*/  

               &SignalFlags);    /\* share warning (return) \*/  

  

    if (error) return(error);  

  

/\* Lock down (freeze the location) of the buffer of notes IDs. Cast  

the resulting pointer to the type we need. \*/  

  

 if (hBuffer != NULLHANDLE)  

   {  

    IdList = (NOTEID far \*)OSLockObject(hBuffer);  

  

/\* Print out the list of all the note IDs in this collection. \*/  

  

    for (i=0; i<NotesFound; i++)  

        printf ("Note ID number %lu is: %lu\n", ++NumNotes,  

                   IdList[i]);  

  

/\* Unlock the list of note IDs. \*/  

  

    OSUnlockObject(hBuffer);  

  

/\* Free the memory allocated by NIFReadEntries. \*/  

  

      OSMemFree(hBuffer);  

      }  

  

/\* repeat loop if more signal flag is set \*/  

  

} while (SignalFlags & SIGNAL\_MORE\_TO\_DO);         

  




 **See Also :**


**[NIFCloseCollection](NIFCloseCollection.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[OSLockObject](OSLockObject.md)**


**[OSMemFree](OSMemFree.md)**


**[OSUnlockObject](OSUnlockObject.md)**


**[SIGNAL\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B5700765BFC)**



----------------------------------------------------------------------------------------------------------


 





