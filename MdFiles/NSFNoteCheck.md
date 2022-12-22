




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




 


**Function : Note**



**NSFNoteCheck** **- Checks
that each item in a note is correctly structured.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCheck(**  

      DHANDLE  note\_handle**);**



**Description :**



This
function examines each item (field) in the note and determines if the items are
correctly formed. In general, the checking involves verifying that the length
of each item matches its data type. For multi-value items, the function checks
that the overall field length is correct for the number of elements in the
list.  

  

This function will not catch every error that can exist within a note.


 


**Parameters :**



Input :  

note\_handle  -  The handle of the note that you want to test.  

  




Output :  

(routine)  -  Returns NOERROR if the note appears to be correctly structured. 
The return codes include:  

  

ERR\_INVALID\_ITEMLEN if an item's overall length does not match its data type.  

  

ERR\_INVALID\_ITEMTYPE if an item's type is not recognized.  

  

ERR\_xxx  which is a STATUS code returned from a lower level Notes function. 
This value can be passed to OSLoadString to obtain a text string that can be
presented in a dialog box or log entry.  

  

  




 




----------------------------------------------------------------------------------------------------------


 





