




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




**Initial Release 7.0.2**



**Function : MIME**



**MMDestroyConvControls** **- destroy a
Conversion Controls context.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



STATUS
LNPUBLIC **MMDestroyConvControls(**  

      CCHANDLE  hCC**);**



**Description :**



The function
MMDestroyConvControls destroys a Conversions Controls context, freeing memory
previously allocated for the conversion configuration settings.


 


 


**Parameters :**



Input :  

hCC  -  a CCHANDLE to a Conversion Controls context created by a previous call
to MMCreateConvControls.  

  




Output :  

(routine)  -  Successfully converted the note.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**



STATUS err;


 


if (err =
MMDestroyConvControls(hCC)) {


        goto exit;


}


 


 **See Also :**


**[CCHANDLE](CCHANDLE.md)**


**[MMCreateConvControls](MMCreateConvControls.md)**



----------------------------------------------------------------------------------------------------------


 





