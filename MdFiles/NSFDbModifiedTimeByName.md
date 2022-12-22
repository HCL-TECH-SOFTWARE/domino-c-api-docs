




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Function : Database**



**NSFDbModifiedTimeByName** **- Get a
database's data/non-data last modified times by DBName.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbModifiedTimeByName(**  

      char \*DbName,  

      TIMEDATE \*retDataModified,  

      TIMEDATE \*retNonDataModified**);**



**Description :**



This
function obtains the time/date of the last modified data and non-data notes in
the specified database.  The same information can also be obtained with
NSFDbOpenExtended.


 


**Parameters :**



Input :  

DbName  -  A pointer to a Domino database name.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully obtained the database's data and non-data last modified
times.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retDataModified  -  The address of a TIMEDATE structure in which the last
modified time/date of the most recently modified data note/document is
returned.  

  

retNonDataModified  -  The address of a TIMEDATE structure in which the last
modified time/date of the most recently modified non-data note/document is
returned.  

  




 **Sample Usage :**


 /\* Get Last modified
time/date for data and non-data notes \*/


TIMEDATE
       retDataModified, retNonDataModified;


char      
\*path\_name;   


   
if (error =
NSFDbModifiedTimeByName(path\_name, &retDataModified,
&retNonDataModified))


   
{


              goto
Exit;


   
        


   
}


 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





