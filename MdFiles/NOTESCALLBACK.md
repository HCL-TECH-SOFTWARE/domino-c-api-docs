




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




 


**Data Type : Mixed 32/16-bit Model**



**NOTESCALLBACK** **-** \* OBSOLETE \*
Calling convention for callback functions


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#define NOTESCALLBACK
LNCALLBACK


 


**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


This macro
defines the calling convention used for callback functions - application
functions called from within Notes.  In the mixed 32/16-bit model for OS/2 2.1,
the application callback functions are 32-bit code.  Notes will attempt to call
the function using the 16-bit Pascal calling convention.  To support this, the
macro specifies that callback functions use the 16-bit "\_Far16
\_Pascal" calling convention.  Under Windows and OS/2 1.x, the calling
convention used is "FAR PASCAL".  On other platforms, this macro is
null;  no special calling convention is used.


 **Sample Usage :**


/\* Notes API include
files \*/  

  

#include <global.h>  

#include <nsfdb.h>  

#include <nsfnote.h>  

#include <nsfsearc.h>  

#include <osmem.h>  

#include <nsferr.h>  

  

  

/\* Global data \*/  

  

STATUS result;  

  

/\* Callback function declaration \*/  

  

STATUS NOTESCALLBACK print\_fields (  

    void         NOTESPTR db\_handle,  

    SEARCH\_MATCH NOTESPTR search\_info,  

    ITEM\_TABLE   NOTESPTR summary\_info  

) {  

        . . .  

}  

  

        . . .  

  

/\* Passing address of the callback to Notes \*/  

  

    result = NSFSearch (  

        db\_handle,      /\* database handle \*/  

        formula\_handle, /\* selection formula \*/  

        NULL,           /\* title of view in selection formula \*/  

        0,              /\* search flags \*/  

        NOTE\_CLASS\_DATA,/\* note class to find \*/  

        NULL,           /\* starting date (unused) \*/  

        print\_fields,   /\* call function for each note found \*/  

        &db\_handle,     /\* argument to print\_fields \*/  

        NULL);          /\* returned ending date (unused) \*/


 **See Also :**


**[LNCALLBACK](LNCALLBACK.md)**


**[NOTESAPI](NOTESAPI.md)**


**[NOTESAPICDECL](NOTESAPICDECL.md)**


**[NOTESCALLBACKPTR](NOTESCALLBACKPTR.md)**


**[NotesMain](NotesMain.md)**



----------------------------------------------------------------------------------------------------------


 





