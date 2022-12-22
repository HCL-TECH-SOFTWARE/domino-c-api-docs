




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



**IDEnumerate** **- Calls
action routine for each ID in an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDEnumerate(**  

      DHANDLE  hTable,  

      IDENUMERATEPROC  Routine,  

      void far \*Parameter**);**



**Description :**



This function
takes a handle to an ID Table, the address of an action routine, and a pointer
of your choosing.  It calls the action routine with each note ID in the ID
Table and the user supplied parameter, until the ID Table is exhausted.  If the
routine returns an error, IDEnumerate will halt and pass it back.  

  

ID Tables are ordered by ID value. IDEnumerate calls the action routine in the
order in which the IDs are stored in the table.


 


**Parameters :**



Input :  

hTable  -  A handle to an ID Table containing the note IDs you wish the action
routine to act on.  

  

Routine  -  A pointer to the action routine.  The action routine must conform
to the calling sequence defined in the following declaration:    

   

STATUS LNPUBLIC Routine(void far \*Parameter, DWORD id);  

  

Parameter  -  A pointer to an object of your choice.  NULL if you do not wish
to take advantage of this feature.  The object could be a database handle,
context/state structure, etc..  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully executed the action routine with each note ID in the ID
Table.  

  

ERR\_xxx - Errors returned by lower level functions, including the action
routine itself.  There are so many possible causes, that it is best to use the
code in a call to OSLoadString and display/log the error for the user.  

  

  




 **Sample Usage :**


            
IDENUMERATEPROC  lpIDProc;  

           lpIDProc = (IDENUMERATEPROC) MakeProcInstance  

               ((FARPROC)TouchNotes);  

           error\_status = IDEnumerate(cpytable\_handle,  

                                      lpIDProc,  

                                      &db\_handle\_src);  

           FreeProcInstance(lpIDProc);  

             

  




 **See Also :**


**[IDENUMERATEPROC](IDENUMERATEPROC.md)**


**[IDCreateTable](IDCreateTable.md)**


**[IDDelete](IDDelete.md)**


**[IDDeleteAll](IDDeleteAll.md)**


**[IDEntries](IDEntries.md)**


**[IDInsert](IDInsert.md)**


**[IDIsPresent](IDIsPresent.md)**


**[IDScan](IDScan.md)**


**[IDTableCopy](IDTableCopy.md)**


**[IDTableSize](IDTableSize.md)**



----------------------------------------------------------------------------------------------------------


 





