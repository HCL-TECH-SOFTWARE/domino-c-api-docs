




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



**Function : Database; DB2**



**NSFDB2ListNSFDB2Databases** **- Provides
a list of all NSFDB2 databases.** 


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2ListNSFDB2Databases(**  

      MEMHANDLE \*hDbList,  

      void far \*\*pDbList,  

      const char far \*tablespaceName**);**



**Description :**



Provides a
list of all NSFDB2 databases.  An NSFDB2 database is a database that you can
work with in DB2 and in Notes/Domino.


 


**Parameters :**



Input :  

  

tablespaceName  -  (optional):   Limits results to NSFDB2 databases in this
tablespace.  Passing NULL will result in a list of all NSFDB2 databases served
by Domino.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successful.  

  

ERR\_DB2NSF\_NOT\_ENABLED\_FOR\_DB2 - The Domino server is not enabled for DB2.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

hDbList  -  Address of a HANDLE in which the handle to the Domino memory object
containing the newly created text LIST is returned.   The list will contain a
file path of all NSFDB2 databases served by Domino.  Upon successful return,
the list memory object is locked and a pointer to the object is returned in
pDbList.  Since the object is returned locked, you must explicitly unlock the
object (OSUnlockObject) before attempting to free it (OSMemFree).   

Use ListGetText(\*pDbList, FALSE, EntryNumber, ....) to obtain each NSFDB2
database file path.  

  

pDbList  -  Pointer to the newly created list of bad link file names.  

  




 **Sample Usage :**


       
MEMHANDLE      hDbList;


 void   far 
\*pDbList;


 STATUS     
rc;


 char       
\*pEntry;


 WORD       
len;


 


 rc =
NSFDB2ListNSFDB2Databases(&hDbList, &pDbList, NULL);


 /\* get the
first NSFDB2 database \*/


 for (int
x=0; x < ListGetNumEntries(hDbList, FALSE); x++)


 {


 


      if (
(ListGetText(pDbList, FALSE, x, \*pEntry, &len)) == NOERROR)


      {


                  printf("%s\n",
)


      }


 }


 OSUnlockObject(hDbList);


 OSMemFree(hDbList);


 **See Also :**


**[ListGetText](ListGetText.md)**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**


**[NSFDB2RegenerateLinks](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/986F1A03FA32C49985256E600055985D)**



----------------------------------------------------------------------------------------------------------


 





