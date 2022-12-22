




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




 


**Function : Database**



**NSFDbFilter** **- Run the
periodic filter on the database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbFilter(**  

      DBHANDLE  hFilterDB,  

      NOTEHANDLE  hFilterNote,  

      DHANDLE  hNotesToFilter,  

      BOOL  fIncremental,  

      void far \*Reserved1,  

      void far \*Reserved2,  

      char far \*DbTitle,  

      char far \*ViewTitle,  

      void far \*Reserved3,  

      void far \*Reserved4,  

      DHANDLE  hDeletedList,  

      DHANDLE  hSelectedList**);**



**Description :**



Run the
specified filter against the specified notes in the database.  


 


**Parameters :**



Input :  

hFilterDB  -  Handle of the database to apply the filter against.  

  

hFilterNote  -  Note handle of the filter note.  

  

hNotesToFilter  -  Handle of note ID table.  If fIncremental is FALSE, this is
the list of notes to operate on.  

  

fIncremental  -  If FALSE, notes specified in the hNotesToFilter ID table are
processed.  If FALSE, the notes specified in the filter note are processed.  

  

Reserved1  -  Reserved;  must be NULL.  

  

Reserved2  -  Reserved;  must be NULL.  

  

DbTitle  -  Optional;  if NULL, the database title is obtained from the
database being processed.  If not NULL, points to a null-terminated string
containing the title to use for this database for the @DbTitle function.  

  

ViewTitle  -  Optional;  if not NULL, points to a null-terminated string
containing the title for the view.  NULL may be used if the database is not
open in the context of a view.  

  

Reserved3  -  Reserved;  must be NULL.  

  

Reserved4  -  Reserved;  must be NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Database successfully opened.  

ERR\_FT\_NOMATCHES - No notes match search criteria.  

ERR\_CANCEL - Search was cancelled.  

ERR\_NOACCESS - Caller does not have access to perform that operation.  

  

  

hNotesToFilter  -  If fIncremental is FALSE, only the notes which satisfy the
filter remain in this ID table.  If fIncremental is TRUE, the original entries
are not modified and the notes which satisfy the filter are added to the ID
table.  

  

hDeletedList  -  If NULLHANDLE is passed, any notes identified by the filter
for deletion are deleted by NSFDbFilter().  If not NULLHANDLE, the IDs of the
notes to be deleted are placed in this ID table and the notes are not deleted
by NSFDbFilter().  

  

hSelectedList  -  If NULLHANDLE, FILTER\_OP\_SELECT is not supported.  If not
NULLHANDLE, IDs of notes selected by the filter are placed in this ID table.  

  




 




----------------------------------------------------------------------------------------------------------


 





