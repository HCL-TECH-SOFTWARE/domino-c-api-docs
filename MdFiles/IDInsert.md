




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




 


**Function : ID Table**



**IDInsert** **- Inserts a
note ID into an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDInsert(**  

      DHANDLE  hTable,  

      DWORD  id,  

      BOOL far \*retfInserted**);**



**Description :**



This
function takes a handle to an ID Table and a note ID. It inserts the ID into
the ID Table only if the table does not already contain that ID.  It returns a
BOOL value in the \*retfInserted parameter indicating whether or not the note ID
was successfully inserted into the ID Table.  A value of FALSE indicates that
the ID Table already contained that ID.  This function also sets the
IDTABLE\_MODIFIED flag if the ID was successfully inserted, that is if the
returned BOOL value is TRUE.      

  

ID Tables are ordered by ID value. IDInsert stores the ID in the table
according to its value.


 


**Parameters :**



Input :  

hTable  -  A handle to the ID Table.  

  

id  -  The ID you wish to insert into the ID Table.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - ID successfully inserted or ID found already in the table.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retfInserted  -  The address of a BOOL variable in which the outcome of the
call to IDInsert is placed.  TRUE - if the specified ID was inserted into the
ID Table.  FALSE - if the ID was already in the ID Table.  Can be NULL if no
return value is required.  

  




 **Sample Usage :**


STATUS LNPUBLIC
AddIDUnique      

            (void \* phNoteIDTable,   

            SEARCH\_MATCH \*search\_info,   

            ITEM\_TABLE \*summary\_info)  

{  

    DHANDLE      hNoteIDTable;  

    STATUS      error;  

    BOOL        flagOK;  

  

    if (!(search\_info->SERetFlags & SE\_FMATCH))     /\* V4 \*/  

        return (NOERROR);  

  

  

    hNoteIDTable = \*((DHANDLE \*)phNoteIDTable);  

  

    if (error = IDInsert(hNoteIDTable, search\_info->ID.NoteID, &flagOK))  

    {  

        printf ("Error: unable to insert note ID into table.\n");  

        return (ERR(error));  

    }  

    if (flagOK == TRUE)  

    {  

        printf ("\tInserted note %lX into table.\n",
search\_info->ID.NoteID);  

    }  

    else  

    {  

        printf ("\tNote %lX is already in table.\n",
search\_info->ID.NoteID);  

    }  

  

    return (NOERROR);  

}


 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDDelete](IDDelete.md)**


**[IDDeleteAll](IDDeleteAll.md)**


**[IDEntries](IDEntries.md)**


**[IDEnumerate](IDEnumerate.md)**


**[IDIsPresent](IDIsPresent.md)**


**[IDScan](IDScan.md)**


**[IDTableCopy](IDTableCopy.md)**


**[IDTableSize](IDTableSize.md)**



----------------------------------------------------------------------------------------------------------


 





