




<!--
 /\* Font Definitions \*/
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




 


**Function : Address Book; Domino
Directory**



**NAMEGetModifiedTime** **- Get last
modified time of Address book(s)**


**----------------------------------------------------------------------------------------------------------**



**#include <lookup.h>**



void
LNPUBLIC **NAMEGetModifiedTime(**  

      TIMEDATE far \*retModified**);**



**Description :**



**Note:**Address books refer to both Notes Client Address books, and Domino
Server Address books know as Domino Directories.


 


       This
function obtains the latest modified time/date of all the Address books in the
process's list. Use this routine to determine if any of the Address books used
by your program have been modified since your program performed a name lookup.  

  

Name lookup functions create a list of collections from the Address books
identified by either the Directory Assistance database (formerly referred to as
the Master Address Book) or the NAMES variable in the notes.ini  file. These
lookup functions cache the list in memory to improve the efficiency of repeated
look ups. NAMEGetModifiedTime loops through this list obtaining the data
modified time/date of each Address book. It returns the latest date found to
the variable specified by retModified.


 


**Parameters :**



Input :  

retModified  -  Address of a variable to receive last modified date/time  

  




Output :  

(routine)  -  None.  

  

  

retModified  -  The last modified time/date of the most recently modified
Address book database  

  




 **See Also :**


**[NAMELookup](NAMELookup.md)**


**[NSFDbModifiedTime](NSFDbModifiedTime.md)**



----------------------------------------------------------------------------------------------------------


 





