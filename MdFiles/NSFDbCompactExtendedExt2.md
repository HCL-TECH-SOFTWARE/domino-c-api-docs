




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




**Initial Release 8.5.2**



**Function : Database**



**NSFDbCompactExtendedExt2** **-
Compresses a local Domino database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCompactExtendedExt2(**  

      const char \*Pathname,  

      DWORD  Options,  

      DWORD  Options2,  

      NUMBER \*OriginalSize,  

      NUMBER \*CompactedSize**);**



**Description :**



This
function compresses a local database  to remove the space left by deleting
documents, freeing up disk space.  Deletion stubs however, are left intact in
the database.  This function is the same as **NSFDbCompactExtended**, but it
allows more options.


 


**Parameters :**



Input :  

Pathname  -  A pointer to the pathname of a Domino database.  The string must
be null-terminated.  The directory part of the path may be omitted if the
database is in the data directory.  The filename extension may be omitted if it
is ".NSF".  

  

Options  -  See DBCOMPACT\_xxx.  If no options are desired, this parameter may
be set to 0 (Zero).  

  

Options2  -  See DBCOMPACT2\_xxx,the parameter to allow customers to turn on/off
design compression, data compression and DAOS for a given database.  

#define DBCOMPACT2\_COMPRESS\_DESIGN\_NS       0x00000400      /\* TRUE if design
note non-summary should be compressed \*/  

#define DBCOMPACT2\_UNCOMPRESS\_DESIGN\_NS  0x00000800      /\* TRUE if design note
non-summary should be uncompressed \*/  

  

#define DBCOMPACT2\_COMPRESS\_DATA\_DOCS      0x00004000      /\* TRUE if all data
note non-summary should be compressed \*/  

#define DBCOMPACT2\_UNCOMPRESS\_DATA\_DOCS 0x00008000      /\* TRUE if all data
note non-summary should be uncompressed \*/  

  

#define DBCOMPACT2\_FORCE\_DAOS\_ON                  0x00020000      /\* enable
compact TO DAOS \*/  

#define DBCOMPACT2\_FORCE\_DAOS\_OFF                0x00040000      /\* enable
compact FROM DAOS \*/  

  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is.  

  

  

OriginalSize  -  Returns the OriginalSize of the database in a NUMBER \*.  

  

CompactedSize  -  Returns the CompactedSize of the database in a NUMBER \*.  

  




 **See Also :**


**[NSFDbCompact](NSFDbCompact.md)**


**[NSFDbCompactExtended](NSFDbCompactExtended.md)**



----------------------------------------------------------------------------------------------------------


 





