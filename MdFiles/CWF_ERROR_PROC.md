




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.0**



**Data Type : Note**



**CWF\_ERROR\_PROC** **-** Pointer to
an error callback function called from NSFNoteComputeWithForm().


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfnote.h>**



**Definition :**



typedef    WORD
(LNCALLBACKPTR CWF\_ERROR\_PROC)(


   const void far
\*pCDField,


   WORD phase,


   STATUS error,


   HANDLE ErrorText,


   WORD wErrorTextSize,


   void far \*ctx);


 


**Description :**



If an error
is found when validating field values in NSFNoteComputeWithForm(), the error
callback function is called with information about the problem.  The arguments
to this callback function are:


 


   pCDField 
- Pointer to the CDField in the form note.


 


   phase    
- Flag indicating the current validation phase.  See CWF\_xxx for possible
values.


 


   error    
- The Domino status code for the error that was detected.


 


   ErrorText
- Handle to memory containing the text that caused the error.  The handle is a
handle to TYPE\_TEXT.  You must get a pointer to the handle by using
OSLockObject.  Note: Domino or Notes will free the memory for this HANDLE.


 


  
wErrorTextSize - Number of bytes in the error text.


 


   ctx -
32-bit "CallersContext" value passed to NSFNoteComputeWithForm().


 


**Note:**  If the
flag CWF\_CONTINUE\_ON\_ERROR is passed in the dwFlags argument of
NSFNoteComputeWithForm(), error processing for fields will be skipped - the
callback function will not be invoked.


 **See Also :**


**[CWF\_xxx (Return Codes)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70D2C510DEF69C6C85256261005D9C2B)**


**[CWF\_xxx (Validation Phases)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E2F5A18E435B5FE985256237005182EE)**


**[NSFNoteComputeWithForm](NSFNoteComputeWithForm.md)**



----------------------------------------------------------------------------------------------------------


 





