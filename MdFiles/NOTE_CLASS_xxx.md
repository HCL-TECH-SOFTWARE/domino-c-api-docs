




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Symbolic Value : Note**



**NOTE\_CLASS\_xxx** **-** Types of
notes.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      NOTE\_CLASS\_DOCUMENT             -  Document (data) note.  

  

      NOTE\_CLASS\_DATA           -  Same as NOTE\_CLASS\_DOCUMENT - used prior to
version 3.0 of the API.  

  

      NOTE\_CLASS\_INFO            -  Database Policy note also known as
Help-About Database document.  

  

      NOTE\_CLASS\_FORM          -  Form note.  

  

      NOTE\_CLASS\_VIEW            -  View or folder note.  

  

      NOTE\_CLASS\_ICON            -  Icon note.  

  

      NOTE\_CLASS\_DESIGN       -  A special view note that is a collection of
all forms, views, macros, and replicaton formulas.  

  

      NOTE\_CLASS\_ACL              -  Access control list note. (This note
contains some information about the access control list. The note does not
contain the access control list itself.)  

  

      NOTE\_CLASS\_HELP\_INDEX            -  Domino built-in help index.  

  

      NOTE\_CLASS\_HELP            -  Database Help note also known as Help-Using
Database document.  

  

      NOTE\_CLASS\_FILTER         -  Macro (filter) note.  

  

      NOTE\_CLASS\_FIELD           -  Shared field note.  

  

      NOTE\_CLASS\_REPLFORMULA       -  Replication formula note.  

  

      NOTE\_CLASS\_PRIVATE      -  Private design note, use $PrivateDesign view
to locate/classify.  

  

      NOTE\_CLASS\_DEFAULT     -  Default note for the class. One note in each
class may be marked with this flag, which indicates that this note is the
default note for that class in this database (for example, a default form note
or a default view note). The Note ID for each default note is stored in a table
in the database. Document notes do not have a default. This flag cannot be used
with NSFSearch; to locate the default form or view note, use
NSFDbGetSpecialNoteID.  

  

      NOTE\_CLASS\_NOTIFYDELETION   -  Set by NSFSearch for deleted note. See
SEARCH\_xxx, SEARCH\_NOTIFYDELETIONS.  

  

      NOTE\_CLASS\_ALL   -  All note types.  

  

      NOTE\_CLASS\_ALLNONDATA          -  All types of notes except data notes.  

  

      NOTE\_CLASS\_NONE           -  No notes.  

  

      NOTE\_CLASS\_SINGLE\_INSTANCE             -  Symbol for those note classes
that allow only one such note in a database: NOTE\_CLASS\_DESIGN | NOTE\_CLASS\_ACL
| NOTE\_CLASS\_INFO | NOTE\_CLASS\_ICON | NOTE\_CLASS\_HELP\_INDEX.  

  




**Description :**



These bit
masks define the types of notes in a database. The bit masks may be or'ed
together to specify more than one type of note.  

  

NOTE\_CLASS\_DESIGN may be bitwise - ORed with NOTE\_ID\_SPECIAL to yield the note
ID of the design collection of the database. This value (NOTE\_CLASS\_DESIGN |
NOTE\_ID\_SPECIAL) may be specified in the ViewNoteID parameter of
NIFOpenCollection to open the design collection. NOTE\_CLASS\_DESIGN may also be
specified in the Index parameter of NSFDbGetSpecialNoteID to get the note ID of
the design collection.


 **Sample Usage :**


    /\*  Open the
special "design" collection, which contains an index of  

        all nondata notes. \*/  

  

    if (error = NIFOpenCollection(hDB,   

                            hDB,   

                            NOTE\_ID\_SPECIAL+NOTE\_CLASS\_DESIGN,  

                            OPEN\_DO\_NOT\_CREATE,  

                            NULLHANDLE,  

                            &hCollection,  

                            NULL, NULL, NULL, NULL))  

   {    /\* Collection may not have been setup yet by the first user to   

        open the file.\*/  

        printf("Unable to open the design collection for '%s'.\n",  

                                         szDBTitle);  

        NSFDbClose (hDB);  

        return(ERR(error));  

    }  

  




 **See Also :**


**[NSFDbCopy](NSFDbCopy.md)**


**[NSFSearch](NSFSearch.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NSFDbGetSpecialNoteID](NSFDbGetSpecialNoteID.md)**



----------------------------------------------------------------------------------------------------------


 





