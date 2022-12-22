




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




 


**Function : ID Table**



**IDTableDifferences** **- Determine
the changes to make to table 1 same as table 2**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS **IDTableDifferences(**  

      DHANDLE  hSrc1Table,  

      DHANDLE  hSrc2Table,  

      DHANDLE \*rethAdds,  

      DHANDLE \*rethDelete,  

      DHANDLE  rethSame**);**



**Description :**



Determine
the changes to make to table 1 same as table 2. table 1 is the original table,
and table 2   needs modification. This is just an optimized version of doing
intersections and deletions. this routine checks for overlap and ensures the
ranges are aligned. If the resulting table is null after the equation
indicates  there is no difference. table will be locked during the routine
execution to avoid accidental alteration 


 


**Parameters :**



Input :  

hSrc1Table  -  source table 1  

  

hSrc2Table  -  source table 2  

  




Output :  

(routine)  -  Routine return status from this call. Either success or whatever
the error is.  

  

  

rethAdds  -  handle of the add table (if addition is determined)  

  

rethDelete  -  handle of deletion table (if deletion is determined)  

  

rethSame  -  handle of the same table   

  




 **Sample Usage :**




               /\*
Assumes hEntryIDTable and hNewIdTable, populated IDTables \*/


 


               DHANDLE
hDeleted = NULLHANDLE;


 


               {


                              error
= IDTableDifferences(hEntryIdTable, hNewIdTable,


                                                                           NULL,


                                                                           &hDeleted,


                                                                           NULL);


 


                                             IDDestroyTable(s\_hEntryIdTable);


                                             s\_hEntryIdTable
= s\_hNewIdTable;


                                             s\_hNewIdTable
= NULLHANDLE;


                              }


 


                              /\*
Process documents found to be deleted \*/


                              if ( NOERROR == error )


                              {


                                             NOTEID NoteId;


                                             BOOL
bFirst = TRUE;


                                             while(
IDScan(hDeleted, bFirst, &NoteId))


                                             {


                                                            bFirst
= FALSE;


                                                            ProcessThisNote(NoteId);


                                             }


                              }


               }


 


               if ( hDeleted )


                              IDDestroyTable(hDeleted);


 


               return error;


}


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





