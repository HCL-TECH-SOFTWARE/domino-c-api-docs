




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




**Initial Release 6**



**Function : Extension Manager**



**NSFArchiveDeleteNotesEMCallback** **- Extension
Manager callback for EM\_NSFARCHIVEDELETENOTES**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **NSFArchiveDeleteNotesEMCallback(**  

      DBHANDLE  hDB,  

      HANDLE  hTempIDTable,  

      DWORD  dwFlags**);**



**Description :**



EM\_NSFARCHIVEDELETENOTES
is called after documents have been selected and copied to the destination
database and it is time for archiving to delete the archived notes that qualify
from the source database.   If  registered with the EM\_REG\_BEFORE flag, the
callback is called before the documents are deleted from the source database. 
If registered with the EM\_REG\_AFTER flag, the callback is called after the
documents have been deleted from the source database.


 


**Parameters :**



Input :  

hDB  -  Handle of the source database where notes will be deleted from.  

  

hTempIDTable  -  Handle of the id table containing the notes ids to be deleted.  

  

dwFlags  -  None at this time.  

  




Output :  

(routine)  -  ERR\_EM\_CONTINUE -  Continue processing.    

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





