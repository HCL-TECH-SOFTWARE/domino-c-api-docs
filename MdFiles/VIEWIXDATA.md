




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




 


**Data Type : Views**



**VIEWIXDATA** **-** Data
structure passed from Notes to view import/export module


**----------------------------------------------------------------------------------------------------------**



**#include
<ixview.h>**



**Definition :**



  

typedef struct


        {


        DHANDLE
hFormNames;                                  /\* handle to array of form names
\*/


        WORD  
FormCount;                                    /\* Number of form names \*/


        WORD  
Reserved1;


        DBHANDLE
hNoteFile;                                  /\* Notes file handle \*/


        DBHANDLE
hViewFile;                                  /\* View file handle \*/


        WORD  
wFlags;                                       /\* Flags, reserved for internal
use \*/


        NOTEID
ViewNoteID;                                   /\* View note ID \*/


        UNID  
ViewNoteUNID;                         /\* View universal note ID \*/


        HCOLLECTION
hViewCollection;          /\* View collection handle \*/


        WORD  
Reserved3;


        DHANDLE
hUnreadList;                                 /\* Unread note ID list handle \*/


        DHANDLE
hCollapsedList;                              /\* Collapsed note ID list handle
\*/


        DHANDLE
hSelectedList;                       /\* Selected note ID list handle \*/


        WORD  
Reserved4;


        FLAG
ViewIsPrivate:1;                        /\* View is private \*/


        NOTEID
CaretNoteID;                          /\* Caret note ID \*/


        WORD
ColumnCount;                                    /\* Number of columns in the
view \*/


        DHANDLE
hColDesc;                                    /\* Column descriptor array
(IXCOLDESC) \*/


        WORD
LineArrayEntrySize;                     /\* Size (in bytes) of a line array
entry \*/


        WORD
TextWidth;                                             /\* Width of text \*/


        WORD
NumTextWidth;                                   /\* Width of numeric text
characters \*/


        WORD
Categories;                                     /\* Number of category columns
in view \*/


        DHANDLE
hFormNoteIDs;                        /\* handle to array of form note IDs \*/


        DHANDLE
hFormNamesFull;                              /\* handle to array of form names
that include synonyms \*/


        /\*
hFormNamesAll points to a list of form names with their synonyms.  A


          
Synonym is created any time a form name is changed.  All the notes


          
created with the previous incarnation of that form have the synonym


          
in their FORM field.  The XSTF export has to know which form the


          
note came from, in order to correctly map the fields to the


          
Agenda data type chosen by the user.


        \*/


        }
VIEWIXDATA;


 


 


**Description :**



Notes passes
this data structure to a view-level import or export module. It contains the
information the view import/export module needs to import document into the
view or export data from the view.  

  

Notes passes a pointer to a data structure of this type as the IXContext input
parameter to a view level import/export module. A view level import/export
module consists of an executable program library that Notes can load and call
when necessary. This library must provide an entry point that Notes can call. The
syntax of this entry point must conform to the IXENTRYPROC definition in
ixview.h.


 **Sample Usage :**



VIEWIXDATA \*ViewData,  

char    \*szStaticText,  

char    \*szItemName1,  

char    \*szItemName2)  

STATUS   error = NOERROR;  

HANDLE   hSelectedList; /\* handle to ID table of Selected notes \*/  

DBHANDLE DbHandle;  

DWORD    notes\_scanned;  /\* used in procedure IDScan() \*/  

NOTEID   note\_id;        /\* gets NOTEIDs stored in ID table \*/  

      

          

hSelectedList = ViewData->hSelectedList;  

if (hSelectedList == NULLHANDLE)  

    return (NOERROR);  

  

DbHandle = ViewData->hNoteFile;  

if (DbHandle == NULLHANDLE)  

    return (NOERROR);  

  

while(IDScan(hSelectedList, (FLAG)(notes\_scanned++==0L), &note\_id))  

{  

    if (error = ReadNote(DbHandle, note\_id,  

                            szStaticText,  

                            szItemName1,  

                            szItemName2))  

    {  

        return(error);  

    }  

}


 **See Also :**


**[IXENTRYPROC](IXENTRYPROC.md)**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[EDITIMPORTDATA](EDITIMPORTDATA.md)**



----------------------------------------------------------------------------------------------------------


 





