




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



**NSFDbReopen** **- Reopens a
database and returns a handle in the caller's address space.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbReopen(**  

      DBHANDLE  hDB,  

      DBHANDLE far \*rethDB**);**



**Description :**



This
function takes a handle to an open database and opens it again, returning a
pointer to a handle that exists in the caller's address space. The calling
routine can then use the new handle to access the database.   

  

This function allows a task (for instance, an API program that is an OLE
server) to access a database that was opened by another task (for instance,
Notes working as an OLE client).   Also, this function allows one thread of a
multithreaded API program to access a database that was already opened by a
different thread.   


 


      To
avoid memory errors, programs should not use database handles from outside the
program's address space for database I/O.


 


**Parameters :**



Input :  

hDB  -  A handle to an open database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Database successfully opened.  

  

ERR\_NOT\_NSF - File is not a database.  

  

ERR\_NSF\_VERSION - Invalid NSF version.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

rethDB  -  The address of a DBHANDLE in which a handle to the reopened
database  is returned.  The calling routine may now use this handle for all
subsequent access to the database or directory.  

  




 **Sample Usage :**


  

// Get DB handle from existing hTempNote from doc info message   

  

    NSFNoteGetInfo(hTempNote, \_NOTE\_DB, &hMyHandleToDB)  

  

// Reopen the database to establish a context to NSF  

  

    if (error = NSFDbReopen(hMyHandleToDB, &hMyTaskDB))  

             :  

        handle error  

             :  

  

// Associate the temp note's DB for the task   

  

    NSFNoteSetInfo(hTempNote, \_NOTE\_DB, &hMyTaskDB)  

            :  

    do whatever you want with the hNote  

           :  

        

// Close the DB to unmap yourself from the DB   

  

    NSFDbClose(hMyTaskDB)  

  




 **See Also :**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





