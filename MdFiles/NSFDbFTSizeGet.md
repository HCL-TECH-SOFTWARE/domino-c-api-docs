




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




**Initial Release 5.0.3**



**Function : Full Text Search**



**NSFDbFTSizeGet** **- Get the
total size of the full text index.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbFTSizeGet(**  

      const char far \*Filename,  

      DWORD \*FTSize**);**



**Description :**



When a
database is full text indexed, an index folder is created in the DATA
directory.  This function retrieves the size of this folder and its contents. 
If the database is not full text indexed, the size will be set to zero.


 


**Parameters :**



Input :  

Filename  -  The name of the database.  

  




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is.   

  

  

FTSize  -  The address of a DWORD in which the total size of a database's full
text index is returned.  If the database is not full text indexed, the size
will be set to zero.  

  




 **Sample Usage :**



 


DWORD
FTSize;


.


.


/\*
Get the size of the Database's full text index file. \*/


 


if
(error = NSFDbFTSizeGet(path\_name, &FTSize))


{


  
print\_api\_error(error);


}


else


{


  
printf("\n FT size is %d\n",FTSize);


}


 **See Also :**


**[FTIndex](FTIndex.md)**


**[FTSearch](FTSearch.md)**


**[FTSearchExt](FTSearchExt.md)**



----------------------------------------------------------------------------------------------------------


 





