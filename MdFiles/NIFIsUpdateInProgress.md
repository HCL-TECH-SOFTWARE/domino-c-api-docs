




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
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
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




}


**Function : Notes/FX data**



**NIFIsUpdateInProgress** **- This
routine checks  the collection is being updated**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



BOOL **NIFIsUpdateInProgress(**  

      HCOLLECTION  hCollection**);**



**Description :**



This routine can be called by callers who want to find out
if the collection is being updated and not perform the update themselves


 


**Parameters :**



Input :  

hCollection  -  per user collection handle context  

  




Output :  

(routine)  -  return TRUE if update is in progress   

  

  




 **Sample Usage :**


STATUS FAR PASCAL
UpdateOpenCollection(DHANDLE hDb, NOTEID NoteID)


{


               HCOLLECTION hCollection;


               WORD    UpdateFlags
= OPEN\_NOUPDATE;


               STATUS error = NOERROR;


 


               /\* Open the
view (with NO UPDATE) and see if updating is currently happening \*/


 


               if (NOERROR ==
NIFOpenCollection(hDb, hDb, NoteID, 


                                                                           UpdateFlags,
NULLHANDLE,


                                                                           &hCollection,


                                                                           NULLHANDLE, NULL, NULL, NULL, NULLHANDLE))


               {


                              if
(!NIFIsUpdateInProgress(hCollection)) 


                                             error
= NIFUpdateCollection(hCollection);


                                             


 


                              NIFCloseCollection(hCollection);


               }


 


               return(error);


}


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





