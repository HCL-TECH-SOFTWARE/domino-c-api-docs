




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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




 


**Function : Access Control List;
Database**



**NSFDbHasFullAccess** **- Check
whether the database handle has full access to the database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



FLAG **NSFDbHasFullAccess(**  

      DBHANDLE  hdb**);**



**Description :**



Check
whether the database handle has full access to perform operations on a
database. Full access is Read, Write, and Edit access as well as the ability
to:


 


*       
Monitor the database.


*       
Replicate the database.


*       
Delete notes from the database.


*       
Delete the database.


*       
Store private folders in the database.


 


**Parameters :**



Input :  

hdb  -  It is an open DB handle.  

  




Output :  

(routine)  -  Returns TRUE if a the database handle has full access to a
database, else returns FALSE.  

  

  




 **Sample Usage :**


      /\* Check DB has full
access. \*/ 


            DBHANDLE
hdb; 


 


            NSFDBOpen(<database
path>, &hdb); 


            if(NSFDbHasFullAccess(hDB))



            { 


                        printf("Can
perform operation that require full access."); 


            } 


            else 


            { 


                        printf("Cannot
perform operations that requires full access."); 


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





