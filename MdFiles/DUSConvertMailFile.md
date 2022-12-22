




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



**Function : Domino Upgrade Services**



**DUSConvertMailFile** **- Converts
Non-Domino mail into Domino mail.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSConvertMailFile(**  

      DHANDLE  hContext,  

      char \*UserName,  

      char \*MailFilePath,  

      NOTEHANDLE  hUserNote,  

      NOTEHANDLE  hNewPersonNote,  

      REGSIGNALPROC  SignalStatus**);**



**Description :**



Once a user
is successfully registered and a Domino mail file is created then
DUSConvertMailFile() will be called to convert the users' existing Non-Domino
mail into Domino mail if the import option fDUSDoMailConversion is turned on.


 


**Parameters :**



Input :  

hContext  -  handle to this DUS' specific context information.  

  

UserName  -  LMBCS string identifying the user being registered, originally
passed in by DUSRetrieveUsers().  

  

MailFilePath  -  LMBCS string identifying the fully qualified mail file path
(including mail server) of the Domino mail file to be created.  

  

hUserNote  -  Contains user specific information.  

  

hNewPersonNote  -  This is a Note handle of the person document in the Domino
Directory (Server's Address book) just created by user registration.  Your
Domino Upgrade Service (DUS) is free to make changes to this note using
NSFNoteUpdate() but the Domino Upgrade Service (DUS) framework will be
responsible for closing the note.  

  

SignalStatus  -  Address of a function to display status in the Status Bar of
the Administration panel located just below the user registration dialog. 
Displaying the progress of the mail conversion may be an example.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[fDUSxxx](fDUSxxx.md)**


**[REGSIGNALPROC](REGSIGNALPROC.md)**



----------------------------------------------------------------------------------------------------------


 





