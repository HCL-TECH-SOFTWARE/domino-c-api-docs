




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




**Initial Release 4.0**



**Function : Views**



**NIFGetLastModifiedTime** **- Get the
collection modification sequence number.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



void
LNPUBLIC **NIFGetLastModifiedTime(**  

      HCOLLECTION  hCollection,  

      TIMEDATE far \*retLastModifiedTime**);**



**Description :**



Each time the
number of documents in a collection is modified, a sequence number is
incremented.  This function will return the modification sequence number, which
may then be compared to a previous value (also obtained by calling
NIFGetLastModifiedTime()) to determine whether or not the number of documents
in the collection has been changed.


 


Note that
the TIMEDATE value returned by this function is not an actual time.


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection.  

  




Output :  

retLastModifiedTime  -  Modification sequence number.  

  




 **See Also :**


**[NIFCloseCollection](NIFCloseCollection.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFUpdateCollection](NIFUpdateCollection.md)**



----------------------------------------------------------------------------------------------------------


 





