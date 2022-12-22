




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




 


**Function : Item (Field)**



**NSFItemScan** **- Calls
action routine for each item found in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS **NSFItemScan(**  

      NOTEHANDLE  note\_handle,  

      NSFITEMSCANPROC  ActionRoutine,  

      void far \*func\_param**);**



**Description :**



This function
finds all the fields in a note. As it does so, NSFItemScan calls a
user-supplied action routine for each field (item) in the note. The action
routine can read the contents of the field, then returns control to NSFItemScan
so the next field can be found.  

  

This function, and your action routine, enables your program to open a note and
determine which items (if any) are present. Then for each field, your program
can find the field's data type, item flags, name, and contents -- all without
knowing the form that was used to create the note.  

  

The action routine can read the contents and properties of each field, but may
not modify a field. This is because the action routine is passed the actual
memory pointers of the field contents, and these should not be modified. If you
want to modify a field, do so with the NSFItemSet\* functions or with
NSFItemDelete/NSFItemAppend. Modify fields only after NSFItemScan has completed
-- not while it is still finding fields.


 


**Parameters :**



Input :  

note\_handle  -  handle to open note, whose items you wish to scan/enumerate in
the action routine.  

  

ActionRoutine  -  Pointer to the routine, that you write, which is called for
each item in a note.  The pointer is of type NSFITEMSCANPROC.  NSFItemScan
calls this routine for every item in the note before returning.  . The routine
has the following prototype:    

  

STATUS LNCALLBACK ActionRoutine(WORD Spare, WORD ItemFlags, char far \*Name,
WORD NameLength,  

                                                            void far \*Value,
DWORD ValueLength, void far \*RoutineParameter);  

  

func\_param  -  An optional void pointer to additional data that can be used by
the action routine.  

  




Output :  

(routine)  -  Return status from the action routine -- indicates either success
or what the error is. The action routine should be coded to at least return the
following codes:  

  

NOERROR - no error occurred in action routine.  

  

ERR\_xxx - Errors returned by lower level functions, including the action
routine itself.   

  

  




 **Sample Usage :**


  

/\* Scan all the fields in the note, calling an action routine for each. \*/  

  

    if (error = NSFItemScan (  

                   note\_handle,   /\* note handle \*/  

                   field\_action,  /\* action routine for fields \*/  

                   &note\_handle)) /\* argument to action routine \*/  

           {  

           NSFNoteClose (note\_handle);  

           return (ERR(error));  

           }  

  

.  

.  

.  

  

  

/\*  

This is the action routine that is called by NSFItemScan for each field in  

the note.  

\*/  

  

STATUS LNCALLOBACK field\_action  

                   (WORD unused,  

                   WORD item\_flags,  

                   char far \*name\_ptr,  

                   WORD name\_len,  

                   void far \*item\_value,  

                   DWORD item\_value\_len,  

                   void far \*note\_handle)  

{  

}  

  

  




 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemQuery](NSFItemQuery.md)**


**[NSFITEMSCANPROC](NSFITEMSCANPROC.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





