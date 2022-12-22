




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




**Initial Release 8.0**



**Function : Name & Address Book**



**NABLookupClose** **- Finish
directory lookup operations by closing a NABLookup object.** 


**----------------------------------------------------------------------------------------------------------**



**#include <nlookup.h>**



void
LNPUBLIC **NABLookupClose(**  

      void \*\*pNABLookup,  

      void \*pNabLookupRecord,  

      DWORD  dwNablookupRecordSize,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Finish
directory lookup operations by closing a NABLookup object that was returned by
a previous NABLookupOpen() call.  Optionally free resources associated with a
NABLookup record that is holding the results of a directory lookup.


 


**Parameters :**



Input :  

pNABLookup  -   location where a pointer to a NABLookup object has been stored
by NABLookupOpen()   

  

pNabLookupRecord  -  (optional)pointer to the structure holding the results of
a directory lookup which should be freed.  

  

dwNablookupRecordSize  -  Size of the structure holding the results of a
directory lookup.  Required if pNabLookupRecord is specified.  

  

dwReserved  -  Must be 0, for future use  

  




Output :  

(routine)  -  None.  

  

  

vpReserved  -  Must be NULL, for future use  

  




 **Sample Usage :**


void
\*pNABLookup = NULL;


NABLOOKUP\_RECORD
LookupEntry = {0};   


/\* this is the struct that holds results of lookup \*/


 


STATUS
error = NABLookupOpen( &pNABLookup, 0, NULL );


            


if
(!error) {


            error
= NABLookupAuthenticatedUser( pNABLookup,


                                                                         
pOrganizationName, /\* set to NULL if none \*/


                                               
pUserDistinguishedName,


                                
               0,


                                               
&LookupEntry,


                                               
sizeof(NABLOOKUP\_RECORD),


                                               
0,


                                               
NULL);


 


if
(!error) {


            /\*
do whatever needs to be done with the user's info in LookupEntry struct \*/


            }


 


/\*
Free the resources, and zero out the LookupEntry struct \*/


 NABLookupClose(
&pNABLookup, &LookupEntry, sizeof(NABLOOKUP\_RECORD), 0, NULL );


            }


 **See Also :**


**[NABLookupAuthenticatedUser](NABLookupAuthenticatedUser.md)**


**[NABLookupOpen](NABLookupOpen.md)**



----------------------------------------------------------------------------------------------------------


 





