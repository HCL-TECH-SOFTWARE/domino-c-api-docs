




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




**Initial Release 6**



**Symbolic Value : Constants; Rich
Text**



**HTML\_EVENT\_CLIENT\_xxx** **-** Specfic HTML
client events.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      HTML\_EVENT\_CLIENT\_FORM\_QUERYOPEN         -  Before the form
is opened  

  

      HTML\_EVENT\_CLIENT\_FORM\_QUERYMODE         -  Before the form is changed to
Read or Edit mode  

  

      HTML\_EVENT\_CLIENT\_FORM\_POSTMODE           -  After the form is changed to
Read or Edit mode  

  

      HTML\_EVENT\_CLIENT\_FORM\_POSTRECALC        -  After the form is refreshed
(and values are recalculated)  

  

      HTML\_EVENT\_CLIENT\_FORM\_POSTSAVE             -  After the form is saved  

  

      HTML\_EVENT\_CLIENT\_FORM\_POSTSEND            -  After the form is sent  

  

      HTML\_EVENT\_CLIENT\_FORM\_QUERYRECALC                 -  Before the form is
refreshed  

  

      HTML\_EVENT\_CLIENT\_FORM\_QUERYSEND          -  Before the form is sent  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYOPEN           -  Before the view is opened  

  

      HTML\_EVENT\_CLIENT\_VIEW\_POSTOPEN             -  After the view is opened  

  

      HTML\_EVENT\_CLIENT\_VIEW\_REGIONDBLCLK      -  Region in a calendar view or
folder is double-clicked  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYOPENDOC   -  Before a document is loaded  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYRECALC       -  Before the view is refreshed  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYADDTOFOLDER       -  Before the document is
added to a folder  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYPASTE         -  Before a paste operation  

  

      HTML\_EVENT\_CLIENT\_VIEW\_POSTPASTE            -  After a paste operation  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYDRAGDROP             -  Before a drag and
drop operation  

  

      HTML\_EVENT\_CLIENT\_VIEW\_POSTDRAGDROP   -  After a drag and drop operation  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYCLOSE         -  The view is being closed  

  

      HTML\_EVENT\_CLIENT\_ONOBJECTEXECUTE        -  Object is activated by an
OLE2 server that is FX/NotesFlow enabled  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYOPEN   -  Before the database is opened  

  

      HTML\_EVENT\_CLIENT\_DB\_POSTOPEN     -  After the database is opened  

  

      HTML\_EVENT\_CLIENT\_DB\_DOCDELETE   -  After a document is deleted (the
document is still available)  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYCLOSE             -  The database is being
closed  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYDELETE           -  Before a document is marked
for deletion  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYUNDELETE      -  Before a document is unmarked
for deletion  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYDRAGDROP     -  Before a drag and drop
operation  

  

      HTML\_EVENT\_CLIENT\_DB\_POSTDRAGDROP       -  After a drag and drop
operation  

  

      HTML\_EVENT\_CLIENT\_VIEW\_QUERYENTRYRESIZE         -  Before a drag
operation in a calendar folder or view  

  

      HTML\_EVENT\_CLIENT\_VIEW\_POSTENTRYRESIZE           -  After a drag
operation in a calendar folder or view  

  

      HTML\_EVENT\_CLIENT\_VIEW\_INVIEWEDIT            -  Relates to in view
editing  

  

      HTML\_EVENT\_CLIENT\_SCHED\_INTERVALCHANGE          -  Relates to a scheduled
interval change event  

  

      HTML\_EVENT\_CLIENT\_DB\_QUERYARCHIVEDRAGDROP   -  Before an archive drag and
drop operation  

  

      HTML\_EVENT\_CLIENT\_DB\_POSTARCHIVEDRAGDROP     -  After an archive drag and
drop operation  

  




 **See Also :**


**[CDEVENT](CDEVENT.md)**



----------------------------------------------------------------------------------------------------------


 





