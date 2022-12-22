




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




 


**Function : index**



**NIFUpdateFilters** **- Check
whether a collection that is open on a remote server is up-to-date.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS **NIFUpdateFilters(**  

      HCOLLECTION  hCollection,  

      WORD  ModifyFlags**);**



**Description :**




Check
whether a collection that is open on a remote server is up-to-date. Call this
routine when making changes to any IDTable index filter (unread list,
expand/collapse list, selected list). 


 


No
handles to the IDTables are required as input since they were established via
NIFOpenCollection. 


 


If
the collection is open on a remote server, then the IDTable lists are re-sent
to the server. If the collection is "local", then the call has no
effect.


 


**Parameters :**



Input :  

hCollection  -  Per user collection context.  

  

ModifyFlags  -  Flags indicating which IDTables were modfied as described in
FILTER\_XXX.  

  




Output :  

(routine)  -  Returns status from the call, either success or an error. The
return codes include:   

NOERROR - Successfully updated the NIF filter.   

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.). There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


      DHANDLE
hUnreadList; 


            STATUS
error; 


 


            if
(error = IDCreateTable(0, &hUnreadList)) 


                        return
error; 


 


            if
(error = NIFOpenCollection( 


                        db\_handle,
/\* Handle of db with view. \*/ 


                        db\_handle,
/\* Handle of db with data. \*/ 


                        ViewID,
/\* Note id of the view. \*/ 


                        0,
/\* Collection open flags. \*/ 


                        hUnreadList,
/\* Handle to unread ID list (input and return). \*/ 


                        &hCollection,
/\* Collection handle (return). \*/ 


                        NULLHANDLE,
/\* Handle to open view note (return). \*/ 


                        NULL,
/\* Universal note id of view (return). \*/ 


                        NULLHANDLE,
/\* Handle to collapsed list (return). \*/ 


                        NULLHANDLE))
/\* Handle to selected list (return). \*/ 


            {



                        NSFDbClose
(db\_handle); 


                        PrintAPIError
(error); 


                        NotesTerm();



                        return
(1); 


            }



            IDInsertRange(hUnreadList,
40, 80, FALSE); //Adding entries into table. 


            if(error
= NIFUpdateFilters(hCollection, FILTER\_UNREAD)) 


            {



                        NIFCloseCollection(hCollection);



                        PrintAPIError
(error); 


                        return
1; 


            }



 **See Also :**




----------------------------------------------------------------------------------------------------------


 





