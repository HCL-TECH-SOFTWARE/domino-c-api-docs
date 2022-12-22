




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




}


**Function : ID Table; IDs; Note**



**NIFGetIDTableExtended** **- Add all
notes of given collection into an ID Table**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS **NIFGetIDTableExtended(**  

      HCOLLECTION  hCollection,  

      WORD  Navigator,  

      DWORD  Flags,  

      DHANDLE  hIDTable**);**



**Description :**



Add all
notes of given collection into an ID Table. This routine cannot be  used in
application that are order dependent since the notes in ID table is completely
unordered. The ID table can be  passed in non-empty if  the user wants to merge
an existing table with collection note IDs


 


**Parameters :**



Input :  

hCollection  -  collection to skim note ID's from  

  

Navigator  -  NIF Read Entries read mask  

  

Flags  -  NIF\_GETIDTABLE\_NOFILTER, NIF\_GETIDTABLE\_RESPONSES\_TOO  

  

hIDTable  -  ID Table to be filled with note id od this collection.  

  




Output :  

(routine)  -  (routine) - error status  

NOERROR  

ERR\_XXX  

  

  




 **Sample Usage :**


STATUS far PASCAL NIFGetIDTable
(HCOLLECTION hCollection,


                                                                                                                        WORD Navigator,


                                                                                                                        DHANDLE hIDTable)


               {


               return(NIFGetIDTableExtended(hCollection, Navigator, 0L, hIDTable));


               }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





