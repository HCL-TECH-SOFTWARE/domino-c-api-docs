




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.5**



**Function : Database**



**NSFDbQuotaGet** **- Return
the database quotas.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbQuotaGet(**  

      const char far \*Filename,  

      DBQUOTAINFO far \*retQuotaInfo**);**



**Description :**



This
function returns the specified database quota information.  This information is
also available from the Notes user interface by choosing menu items File -
Tools - Server Administration to bring up Domino Administrator.  Next, click on
the File tab and select a database, then choose Files - Quotas from the menu to
see the quota settings dialog.


 


**Parameters :**



Input :  

Filename  -  A pointer to the pathname of a Notes database. The string must be
null-terminated.  

  

For a database: The directory part of the path may be omitted if the database
is in the Notes data directory.  If the database is on a remote server, a full
network pathname must be built with OSPathNetConstruct.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully obtained quota information.  

  

ERR\_NO\_SERVER\_ACCESS - You are not authorized to use the server.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

retQuotaInfo  -  Pointer to the returned DBQUOTAINFO structure.  This structure
contains the warning threshold, database size limit, current database size, and
maximum database size.  If no warning threshold is set, zero is returned for
the WarningThreshold member of this structure.  If no database size limit is
set, zero is returned for the SizeLimit member of this structure.  This
structure is allocated by the caller.  

  




 **Sample Usage :**


char       
\*path\_name;          /\* pathname of database \*/


 
STATUS      error = NOERROR;  

  DBQUOTAINFO  dbQuotaStruct;  

  char szErrorString[256];


   


/\*  Program
initialization \*/


/\*  ...                   
\*/            


 


  /\* Get
the DB Quota information \*/  

  error = NSFDbQuotaGet(path\_name, &dbQuotaStruct);  

  if (error)  

  {  

    OSLoadString(0, ERR(error), szErrorString, 255);  

    printf ("Error from NSFDbQuotaGet:  %s\n\n", szErrorString);  

  }  

  else  

  {  

    printf("WarningThreshold:  %lu      SizeLimit:  %lu\n",  

           dbQuotaStruct.WarningThreshold, dbQuotaStruct.SizeLimit);  

    printf("CurrentSize  %lu      MaxDbSize:  %lu\n",  

           dbQuotaStruct.CurrentDbSize, dbQuotaStruct.MaxDbSize);  

  }


/\*  Program
termination \*/


/\* 
...                    \*/   

  




 **See Also :**


**[DBQUOTAINFO](DBQUOTAINFO.md)**


**[NSFDbQuotaSetExt](NSFDbQuotaSetExt.md)**



----------------------------------------------------------------------------------------------------------


 





