




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




**Initial Release 5.0**



**Function : LotusScript**



**NSFNoteLSCompile** **- Compile a
note containing LotusScript modules.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteLSCompile(**  

      DBHANDLE  hDb,  

      NOTEHANDLE  hNote,  

      DWORD  dwFlags**);**



**Description :**



The API
compiles all the LotusScript code found in a design document.  This includes
document classes such as Views, Agents, Forms, Pages, Navigators, Shared
fields,  script libraries, Help documents, using database documents, etc.  It
is a way of making sure that the object code of the script is up-to-date.  


 


For the
Agent note, the compiled object code is saved in the $AssistAction\_Ex item.


 


**Parameters :**



Input :  

hDb  -  Handle to the database.  

  

hNote  -  Handle to the note containing LotusScript modules.  

  

dwFlags  -  (Reserved for future use) Must be 0.  

  

  




Output :  

(routine)  -  (routine)  -  Return indicates either success or what the error
is. The return codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_NULL\_NOTEHANDLE -  if hNote was not specified.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  

  

  




 **Sample Usage :**


 


...


/\* 
Compile the Agent note \*/       


if
(error=NSFNoteLSCompile(hDb,hAgent,0))


{


  
printf("Error: LS Compile\n");


  
goto Exit1;


}


 


/\* 
Update the note \*/


if
(error=NSFNoteUpdate(hAgent,0))


{


  
printf("Error: can't update note after LS Compile\n");


  
goto Exit1;


}


 


 




----------------------------------------------------------------------------------------------------------


 





