




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



**Function : Data Manipulation; Note**



**NSFNoteContract** **- Compress
range/list types in a note to simple data types.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteContract(**  

      NOTEHANDLE  hNote**);**



**Description :**



This
function will compress data in a note to simple data types.  If the following
types have a length of 1, NSFNoteContract will convert the type into the
corresponding simple data type.


 


Type:
TYPE\_TEXT\_LIST                            Length: 1          Simple Data
Type:TYPE\_TEXT


Type:
TYPE\_NUMBER\_RANGE                  Length:1           Simple Data Type:
TYPE\_NUMBER


Type:
TYPE\_TIME\_RANGE            Length:1           Simple Data Type: TYPE\_TIME


 


**Parameters :**



Input :  

hNote  -  A NOTEHANDLE to an existing note.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Note successfully copied.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **See Also :**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





