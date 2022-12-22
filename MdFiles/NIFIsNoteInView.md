




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




 


**Function : ID Table; Views**



**NIFIsNoteInView** **- Check
whether a note ID is in a given view.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS **NIFIsNoteInView(**  

      HCOLLECTION  hCollection,  

      NOTEID  NoteID,  

      BOOL \*retInView**);**



**Description :**



Check
whether a note ID is in a given view and whether the caller has the privileges
to see it. If there is an ID table for the collection and the note is not in
the table, then the note is not in the view. If  there is no ID table for the
collection or if access to a note needs to be checked, then this routine checks
a note by looking it up in the note ID index.  


 


**Parameters :**



Input :  

hCollection  -  Handle of per user collection context  

  

NoteID  -  NoteID being tested  

  




Output :  

(routine)  -  Error status  

NOERROR - if success  

ERR\_XXX - Error ID if fails  

  

  

retInView  -  Place to receive boolean indicator if note is in view.  

  




 **Sample Usage :**




BOOL
Filter(DWORD noteid, STATUS \*retErr)


{


            BOOL
disqualify=FALSE;


            BOOL
bInView;


            


            const STATUS error =
NIFIsNoteInView(hColl, noteid, &bInView);


            if (error != NOERROR)


            {


                        if
(retErr != NULL)


                                    \*retErr
= err;


 


                        xprintf("NIFIsNoteInView
failed [%e] for NoteID %d", err, noteid);


                        return FALSE;


            }


            


            return
bInView;


}


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





