




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




 


**Symbolic Value : Miscellaneous**



**SEARCH\_xxx** **-** NSFSearch()
- SearchFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**


 **Symbolic Values :**      SEARCH\_ALL\_VERSIONS    -  Include deleted and non-matching
notes in the search. (This is always ON for time-delimited searches.)  

  

      SEARCH\_SUMMARY           -  Return summary buffer with each match. If
this flag is not set, the ITEM\_TABLE far \*SummaryBuffer input parameter to the
action routine is NULL.  

  

      SEARCH\_FILETYPE             -  Search a directory instead of a database.  

  

      SEARCH\_NOTIFYDELETIONS         -  Set NOTE\_CLASS\_NOTIFYDELETION bit of
NOTE\_CLASS for deleted notes.  

  

      SEARCH\_ALLPRIVS             -  Return an error if we don't have full
privileges for this search.  

  

      SEARCH\_SESSION\_USERNAME     -  Use current session's user name, not server's.  

  

      SEARCH\_NOABSTRACTS   -  Filter out "Truncated" documents.  

  

      SEARCH\_DATAONLY\_FORMULA    -  Search formula applies only to data notes,
i.e., others match.  

  




**Description :**



Use these
flags in the search\_flags parameter to NSFSearch to control what the function
searches for and what information it returns. These values can be bitwise-ORed
together to combine functionality.


 **Sample Usage :**


  

    if (error = NSFSearch (  

        db\_handle,          /\* database handle \*/  

        NULLHANDLE,         /\* selection formula \*/  

        NULL,               /\* title of view in selection formula \*/  

        SEARCH\_SUMMARY,     /\* search flags: get summary data! \*/  

        NOTE\_CLASS\_DOCUMENT,    /\* note class to find \*/  

        NULL,               /\* starting date (unused) \*/  

        ReadSummaryData,    /\* action routine for notes found \*/  

        NULL,               /\* argument to action routine \*/  

        NULL))              /\* returned ending date (unused) \*/  

  

    {  

        printf ("Error: unable to search database.\n");  

        NSFDbClose (db\_handle);  

        return (ERR(error));  

    }


 **See Also :**


**[NSFSearch](NSFSearch.md)**



----------------------------------------------------------------------------------------------------------


 





