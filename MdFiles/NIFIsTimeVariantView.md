




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




 


**Function : Views**



**NIFIsTimeVariantView** **- Check
whether a view is a time variant view.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



BOOL **NIFIsTimeVariantView(**  

      HCOLLECTION  hCollection**);**



**Description :**



Checks
whether the view is a time-varying view or any type of view that is rebuilt on
each open, for example, a soft deleted view. 


 


**Parameters :**



Input :  

hCollection  -  Per-user colletion context handle.  

  




Output :  

(routine)  -  TRUE if the given view is timevariant view, one that must be
rebuilt each time it is opened.  

  

  




 **Sample Usage :**



            /\*
Presumes hCollection, a COLLECTIONHANDLE for an open view and NoteID, its
design note NOTEID \*/


 


            if (
NIFIsTimeVariantView(hCollection) )


            {


                        xprintf("We
have a time variant view for NoteID %x\n",  NoteID);


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





