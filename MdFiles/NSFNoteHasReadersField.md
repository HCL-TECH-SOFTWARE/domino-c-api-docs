




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




 


**Function : Item (Field); Note**



**NSFNoteHasReadersField** **- Check
whether a note has a readers field.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL **NSFNoteHasReadersField(**  

      DHANDLE  hnote,  

      BLOCKID  retbhItem**);**



**Description :**



Scan all
items in a note and check whether the note has at least one item type that is
ITEM\_READERS.


 


**Parameters :**



Input :  

hnote  -  It is an open Note handle.  

  




Output :  

(routine)  -  Returns TRUE, if note has at least one item type ITEM\_READERS.   

                   FALSE, if no ITEM\_READERS type present.  

  

  

retbhItem  -  If ITEM\_READERS field is present then the BLOCKID of first object
item is returned.  

  




 **Sample Usage :**


      /\*
hnote is an opened document of NOTEHANDLE type. \*/ 


            BLOCKID
bhRFItem; /\* Store block id of first item with readers type. \*/ 


            if
(NSFNoteHasReadersField(hnote, &bhRFItem)) 


            {



                        printf("Document
has at least one reader field"); 


            }



            else



            {



                        printf("Document
has no reader fields"); 


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





