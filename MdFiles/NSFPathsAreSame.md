




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




 


**Function :** 



**NSFPathsAreSame** **- Routine
to see if   paths are the same**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



BOOL **NSFPathsAreSame(**  

      const char\*pNetPath1,  

      WORD  NetPathLen1,  

      const char\*pNetPath2,  

      WORD  NetPathLen2,  

      BOOL  MatchFlatToHierarchical**);**



**Description :**



This routine
to see if paths are the same. The Path contains server name, path and
filename   


If
the comparison  fails, and only one of the paths is specified with a common
name, the


      
names are compared again just using the common names of the servers.


 


     
MatchFlatToHierarchical -  is TRUE then comparison fails are flat will result
in comparison on hierarchical names. 


  



     
Ex. Input1 -  "CN=Jack Aubrey/O=CAM/P=Red Squadron/A=RN/C=GB" 


            
Input2 - "CN=Jack Aubrey/O=CAM/P=Red Squadron/A=RN/C=GB" 


  



   
Hierarchical comparison is to compare  on "O=CAM/P=Red
Squadron/A=RN/C=GB"


 


 


**Parameters :**



Input :  

pNetPath1  -  Server path and filename of notes file  

  

NetPathLen1  -  length of path1 or MAXWORD to calculate  

  

pNetPath2  -  Server path and file name of notes file  

  

NetPathLen2  -  length of path2 or MAXWORD to calculate  

  

MatchFlatToHierarchical  -  Makes hierarchical comparison on paths if it is
TRUE  

  




Output :  

(routine)  -  TRUE - Paths are same  

     FALSE - Paths are different  

  

  




 **Sample Usage :**


if
(NSFPathsAreSame("CN=Jack Aubrey/O=CAM/P=Red Squadron/A=RN/C=GB", 
"CN=Jack Aubrey/O=CAM/P=Red Squadron/A=RN/C=GB", TRUE))


      {


         
//Both net work server paths are identical


       }


       else


       {


         
//Both paths are not identical


        }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





