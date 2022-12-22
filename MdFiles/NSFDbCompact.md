




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



**NSFDbCompact** **-
Compresses a local Domino database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCompact(**  

      const char far \*Pathname,  

      WORD  Options,  

      DWORD far \*retStats**);**



**Description :**



This
function compresses a local database  to remove the space left by deleting
documents, freeing up disk space.  Deletion stubs however, are left intact in
the database.


 


**Parameters :**



Input :  

Pathname  -  A pointer to the pathname of a Domino database.  The string must
be null-terminated.  The directory part of the path may be omitted if the
database is in the data directory.  The filename extension may be omitted if it
is ".NSF".  

  

Options  -  Optional.  Specify DBCOMPACT\_MAILBOX to compact a mail.box file. 
Otherwise, this parameter should be set to 0 (Zero).  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR  

  

ERR\_NOT\_NSF  

  

ERR\_NSF\_VERSION  

  

ERR\_NOT\_LOCAL - An attempt was made to compact a non-local Domino database.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

retStats  -  A pointer to an array of two DWORDs in which database statistics
are returned.  The first DWORD contains the size in bytes of the Domino
database before being compacted, while the second DWORD contains the size of
the database after being compacted.  

  




 **Sample Usage :**


  

char         \*db\_filename;  /\* pathname of source database \*/  

STATUS       error;         /\* return status from API calls \*/  

WORD         Options = 0;   /\* compact options \*/  

DWORD        Stats[2];      /\* status return code \*/  

  

/\* set db\_filename to the name of the database to be compacted \*/  

  

if (error = NSFDbCompact (db\_filename, Options, &Stats[0]))  

   {  

   printf ("error = %x\n", ERR(error));  

   return (ERR(error));  

   }  

printf ("\nCompaction of %s completed\n", db\_filename);  

printf ("Size of %s before compaction:  %lu\n", db\_filename,
Stats[0]);  

printf ("Size of %s after compaction:   %lu\n", db\_filename,
Stats[1]);  

  




 **See Also :**


**[DBCOMPACT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FE0FA3546C7FA616852563610066ED16)**



----------------------------------------------------------------------------------------------------------


 





