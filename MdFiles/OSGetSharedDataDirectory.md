




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




 


**Function : OS File**



**OSGetSharedDataDirectory** **- If a
shared data directory is used, get its path.**


**----------------------------------------------------------------------------------------------------------**



**#include <osfile.h>**



WORD **OSGetSharedDataDirectory(**  

      char \*retPathName**);**



**Description :**



If a shared
directory is used, get the name and length of the shared directory. A length of
zero indicates there is no shared directory defined. A shared data directory is
used to store templates, help files, and other shared components used in
Notes/Domino installation and configuration. 


 


**Parameters :**



Input :  

retPathName  -  Holds templates, help files, etc.  

  




Output :  

(routine)  -  Returns length of the directory name. Returns zero if there is no
shared directory.  

  

  




 **Sample Usage :**


      char
FilePath[MAXPATH] = { 0 }; 


 


            if
(OSGetSharedDataDirectory(FilePath) != 0) 


            {



                        OSPathConstruct(FilePath,
"pubnames.ntf", FilePath); 


                        if
(OSFileOpenRead(FilePath, &fd)) 


                                    return;



            }



 **See Also :**




----------------------------------------------------------------------------------------------------------


 





