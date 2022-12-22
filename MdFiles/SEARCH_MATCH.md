




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




 


**Data Type : Item (Field) Information**



**SEARCH\_MATCH** **-** Information
about each note found by NSFSearch.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfsearc.h>**



**Definition :**



typedef struct {  

   GLOBALINSTANCEID ID; /\* identity of the note within the file \*/  

   ORIGINATORID OriginatorID; /\* identity of the note in the


                          
universe \*/  

   WORD NoteClass;      /\* class of the note \*/  

   BYTE SERetFlags;     /\* match indicator \*/  

   BYTE Privileges;     /\* note privileges \*/  

   WORD SummaryLength;  /\* summary information length \*/  

/\* now comes an ITEM\_TABLE with summary info... \*/  

} SEARCH\_MATCH;


 


**Description :**



NSFSearch
fills this structure with information about each note that it finds, and passes
it as input to the user-supplied action routine.  

  

The second parameter to the NSFSearch action routine is a pointer to this
structure.  

  

Note 1: before accessing members of the SEARCH\_MATCH data structure, your
action routine should use memcpy to copy the structure from the address
specified by the pointer to a variable of type SEARCH\_MATCH. The reason is that
Domino data resides in packed memory buffers. On non-Intel architecture
platforms, the SEARCH\_MATCH pointer provided by Domino may not be aligned
properly for the SEARCH\_MATCH data type. In this case, directly accessing the
members of the SEARCH\_MATCH structure via the pointer may cause a bus error
trap.  

  

Note 2: your action routine should check that the SE\_FMATCH bit is set in the
"SERetFlags" member of the SEARCH\_MATCH structure to ensure that the
note is valid and really matches the search criteria. Non-matching notes
(including deletion stubs) are passed to the action routine when using either a
formula or a search by time/date (or both).  The SE\_FTRUNCATED bit will be set
if the document has been truncated.  

  

Note 3:  The use of the "match" bits has changed from Release 3 to
Release 4 of Notes.  In Release 3, only the values SE\_FNOMATCH or SE\_FMATCH
would be returned in the field "MatchesFormula".  In Release 4,
another bit has been defined, SE\_FTRUNCATED.  Applications which have not been
recompiled will continue to work as they have before;  documents that have been
truncated will not match either SE\_FNOMATCH or SE\_FMATCH.  When applications
are recompiled, the new field name must be used.  The application should now
check for the SE\_FMATCH bit.


 **Sample Usage :**


STATUS LNPUBLIC
ReadSummaryData  

            (VOID far \*optional\_param,  

            SEARCH\_MATCH far \*search\_info,  

            ITEM\_TABLE far \*summary\_info)  

{  

    SEARCH\_MATCH  SearchMatch;  

    STATUS        error;  

  

    memcpy ((char\*)(&SearchMatch), (char \*)search\_info,  

        sizeof(SEARCH\_MATCH));  

  

    if (!(SearchMatch.SERetFlags & SE\_FMATCH))  

        return (NOERROR);  

  

    /\* Print the note ID. \*/  

  

    printf ("\nNote ID is: %#010lx.\n", SearchMatch.ID.NoteID);


 **See Also :**


**[NSFSearch](NSFSearch.md)**


**[SEARCH\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4B004EBF15)**



----------------------------------------------------------------------------------------------------------


 





