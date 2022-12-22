




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



**Function : Backup; Database; DB2**



**NSFDB2GetDbInfoValidity** **- Validate
NSFDB2 database information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2GetDbInfoValidity(**  

      const char \*filePath,  

      char \*Schema,  

      DWORD  szSchema,  

      char \*tableSpace,  

      DWORD  szTableSpace,  

      char \*actualTableSpace,  

      DWORD  szActualTableSpace,  

      BOOL \*schemaExists,  

      BOOL \*tsExists,  

      BOOL \*tsMismatch,  

      DWORD  flags**);**



**Description :**



This
function returns the schema  and table space that Domino believes the specified
NSFDB2 database exists in.  It also returns a status of whether or not the
schema and table space exists.  


 


**Parameters :**



Input :  

filePath  -  The file name of the NSFDB2 database.  

  

szSchema  -  The size of the buffer allocated for Schema.  

  

szTableSpace  -  The size of the buffer allocated for tableSpace.  

  

szActualTableSpace  -  The size of the buffer allocated for actualTableSpace.  

  

flags  -  (Reserved for future use.)  Must be 0.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successful.  

  

ERR\_DB2NSF\_CLI\_ERROR - Internal DB2/CLI error.  

  

ERR\_NOT\_FOUND - NSFDB2 information could not be found for filePath  

  

ERR\_DB2NSF\_NOT\_ENABLED\_FOR\_DB2 - The Domino server is not enabled for DB2.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

Schema  -  The name of the DB2 schema containing the tables for the NSFDB2 db.  

  

tableSpace  -  The name of the table space as recorded in Domino's CATALOG
table.  

  

actualTableSpace  -  The real container location (table space) of
Schema.NSFNOTE  

  

schemaExists  -  True if the Schema specified in Domino's CATALOG table exists.  

  

tsExists  -  True if the table space referenced in Domino's CATALOG table
exists.  

  

tsMismatch  -  True if the table space actually containing Schema.NSFNOTE
differs from what Domino's CATALOG table has listed for filePath.  This will
only happen with DBA intervention or through backup/restore scenarios (e.g.
renaming a table space from the DB2 Control Center application)  

  




 **See Also :**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**


**[NSFDB2ListNSFDB2Databases](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A57AF7CF730AA01685256E6000560BE5)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**



----------------------------------------------------------------------------------------------------------


 





