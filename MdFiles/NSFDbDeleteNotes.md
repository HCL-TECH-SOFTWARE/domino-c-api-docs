




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



**NSFDbDeleteNotes** **- Deletes
all notes in an ID table from a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbDeleteNotes(**  

      DBHANDLE  hDB,  

      DHANDLE  hTable,  

      UNID far \*retUNIDArray**);**



**Description :**



This
function takes a database handle, a handle associated with a Note ID Table, and
deletes all the notes specified in the ID table.  For local databases only, it
also optionally returns an array of UNIDs of the deleted notes (mostly used by
the Replication process).  

  

This function is useful when deleting a large number of notes in a remote
database, because it minimizes the network traffic by sending only one request
to the Lotus Domino Server.


 


Note: This
function will return an error if the ID table contains View notes or Design
notes.


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  

hTable  -  A HANDLE to an ID table containing the IDs you wish to have deleted
from the Domino database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully deleted the notes contained in the ID Table from the
database.  

ERR\_REMOTE\_UNID - (you cannot obtain the UNIDs using this call to remote
databases).  

ERR\_VIEW\_UPDATE - (you cannot delete View notes or Design notes using this
call).  

ERR\_NO\_DELETED\_NOTES - No documents were deleted.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retUNIDArray  -  The address of an array of UNID structures in which the UNIDs
of the deleted notes are returned.  Specify NULL if you do not wish this
information to be returned.  The number of notes in the ID table should not
exceed the number of available elements in the UNID array.  In the case of an
ID in the table which represents a Category (and not a real note), the
corresponding UNID is not returned in the array.  The UNIDs are returned in
Domino canonical format.  

  




 **Sample Usage :**


  

            /\* Batch any Deletions \*/  

   

           if (error\_status = IDCreateTable( alignment,  

                                              &deltable\_handle))  

                goto Exit;  

            else  

                cleanup\_state += FREE\_DELTABLE;  

            del\_max = IDEntries(thetable\_handle);  

            del\_count = 0L;  

            while( del\_count < del\_max )  

            {  

                while (IDScan(thetable\_handle,  

                             (BOOL)(del\_count++==0L), &note\_id))  

                {  

  

                    /\* Build a table to batch operation \*/  

  

                    error\_status = IDInsert(deltable\_handle,  

                                            note\_id, &ok\_flag);  

                    if (!ok\_flag || error\_status)  

                    {  

                        printf("IDInsert in deltable failed.\n");  

                        goto Exit;  

                    }  

                    if ((del\_count % MAXOPTIMALDELETIONS) == 0)  

                        break;  

                }  

                if (IDEntries(deltable\_handle))  

  

                {   /\* Using NULL in 3rd arg avoids ERR\_REMOTE\_UNID \*/  

  

                    if (error\_status = NSFDbDeleteNotes (  

                                            db\_handle\_src,  

                                            deltable\_handle,  

                                            NULL))  

                        goto Exit;  

  

                    /\* adjust del\_count exit of while(IDScan) \*/  

  

                    printf("\n%s: %lu Notes in %s\n",  

                           (del\_count <= del\_max)? "Deleting"  

                                                 : "Deleted",  

                           (del\_count <= del\_max)? 50  

                                                 : del\_count-1,  

                           src\_name);  

                    if (error\_status = IDDeleteAll(deltable\_handle))  

                        goto Exit;  

                }  

            }  

  

            cleanup\_state -= FREE\_DELTABLE;  

            if ( error\_status = IDDestroyTable(deltable\_handle))  

                 goto Exit;  

  




 **See Also :**


**[IDDeleteAll](IDDeleteAll.md)**


**[IDEnumerate](IDEnumerate.md)**


**[IDScan](IDScan.md)**


**[NSFDbGetModifiedNoteTable](NSFDbGetModifiedNoteTable.md)**


**[NSFDbStampNotes](NSFDbStampNotes.md)**



----------------------------------------------------------------------------------------------------------


 





