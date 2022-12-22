




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




**Initial Release 8.0**



**Function : Name & Address Book**



**NABLookupOpen** **- Prepare
to do directory lookup operations by creating a NABLookup object.**


**----------------------------------------------------------------------------------------------------------**



**#include <nlookup.h>**



STATUS
LNPUBLIC **NABLookupOpen(**  

      void \*\*retpNABLookup,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Prepare to
do directory lookup operations by creating a NABLookup object.  For example,
call NABLookupOpen() in order to prepare for calling
NABLookupAuthenticatedUser(), which takes a NABLookup object as an input
parameter.  If NABLookupOpen() succeeds, the caller should eventually call
NABLookupClose() to free resources.


 


**Parameters :**



Input :  

  

dwReserved  -  Must be 0, for future use.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Success.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retpNABLookup  -  location where a pointer to a NABLookup object can be stored.  

  

vpReserved  -  Must be NULL, for future use.  

  




 **Sample Usage :**


void \*pNABLookup =
NULL;


STATUS
error = NABLookupOpen (&pNABLookup, 0, NULL);


 


if (error)


  goto
Done;


 **See Also :**


**[NABLookupAuthenticatedUser](NABLookupAuthenticatedUser.md)**


**[NABLookupClose](NABLookupClose.md)**



----------------------------------------------------------------------------------------------------------


 





