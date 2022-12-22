




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




**Initial Release 5.0.4**



**Function : Database**



**NSFDbSpaceUsageScaled** **- Returns
information about the usage of space in a database in granules.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbSpaceUsageScaled(**  

      DBHANDLE  hDB,  

      DWORD far \*retAllocatedGranules,  

      DWORD far \*retFreeGranules,  

      DWORD far \*retGranularity**);**



**Description :**



This
function returns the number of granules allocated, the number of granules free,
and the granularity size in a specified database.


Granules
relate to the number of bits in space allocation instead of the number of
bytes.  By multiplying the granules allocated by the granularity size, and the
granules free by the granularity size, the result will be in bytes allocated
and free.  Please see the function NSFDbSpaceUsage for more information.


 


**Parameters :**



Input :  

hDB  -  Handle to the database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - success  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that  it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retAllocatedGranules  -  Pointer to the returned number of granules allocated
in the database.  

  

retFreeGranules  -  Pointer to the returned number of granules free in the
database.  

  

retGranularity  -  Pointer to the granularity size of the database.  

  




 **See Also :**


**[NSFDbSpaceUsage](NSFDbSpaceUsage.md)**



----------------------------------------------------------------------------------------------------------


 





