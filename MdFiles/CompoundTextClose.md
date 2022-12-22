




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




 


**Function : Compound Text**



**CompoundTextClose** **- Closes a
CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextClose(**  

      DHANDLE  hCompound,  

      DHANDLE far \*phReturnBuffer,  

      DWORD far \*pdwReturnBufferSize,  

      char far \*pchReturnFile,  

      WORD  wReturnFileNameSize**);**



**Description :**



This routine
closes a CompoundText context.  The behavior of this function depends upon
whether the CompoundText context was created as a StandaloneContext or as an
ItemContext.  

  

**ItemContext**  

  

When closing an ItemContext, only the hCompound parameter should be specified. 
All other parameters should be NULL or 0:  

  

      nError = CompoundTextClose (hCompound, NULL, NULL, NULL, 0);  

  

If nError is not equal to NOERROR, the CompoundTextDiscard routine must be
called as part of the error processing in order to free the resources allocated
by the CompoundText Context.   

  

Recall that an ItemContext is associated with a Domino document.  Use
NSFNoteUpdate after CompoundTextClose to update and save the document.  

  

  

**StandaloneContext**  

  

When closing a StandaloneContext, all parameters should be specified.  The
contents of the StandaloneContext is returned in either a buffer or a file.  

  

If the contents of the StandaloneContext fits in a single segment of memory (less
than 64K bytes), then a handle to a buffer will be returned in the
phReturnBuffer parameter and the size of the data stored in the buffer will be
returned in the pdwReturnBufferSize parameter.  

  

If the contents of the StandaloneContext does not fit in a single segment of
memory, the contents will be written to a temporary file.  In this case, the
string pointed to by pchReturnFile gets the name of the temporary file,
phReturnBuffer gets NULLHANDLE, and pdwReturnBufferSize gets zero.  

  

The returned buffer or file is a monolithic TYPE\_COMPOSITE item.  The buffer or
file begins with the data type word.  The data type word is always in Host
format.  The remainder of the data is in Domino Canonical format.  

  

When this routine returns any error code other than NOERROR, the
CompoundTextDiscard routine must be called as part of the error processing in
order to free the resources allocated by the CompoundText Context.  

  

With StandaloneContext, the caller is responsible for freeing the buffer or
deleting the file that was returned by this routine.


 


**Parameters :**



Input :  

hCompound  -  Handle of the CompoundText context to close.  

  

wReturnFileNameSize  -  Size of buffer pointed to by the pchReturnFile
parameter.  This parameter should be specified as 0 if an ItemContext is being
closed.  

  




Output :  

(routine)  -   Return status from this call:   

  

NOERROR - Successfully closed the CompoundText context.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

phReturnBuffer  -  Pointer to a HANDLE where the handle of the buffer 
containing the TYPE\_COMPOSITE item will be returned; NULLHANDLE when the data
is returned in a file.  This parameter should be specified as NULL if an
ItemContext is being closed.  

  

pdwReturnBufferSize  -  Pointer to a DWORD where the number of bytes in the
buffer will be returned.  This parameter should be specified as NULL if an
ItemContext is being closed.  

  

pchReturnFile  -  Pointer to a buffer where the fully qualified path name of
the file containing the TYPE\_COMPOSITE item will be returned.  This buffer
should have size MAXPATH. This parameter should be specified as NULL if an
ItemContext is being closed.  

  




 **Sample Usage :**


  

STATUS    Status;  

DWORD     dwReturnCDSize;  

DHANDLE    hCompound, hReturnCD;  

char      achReturnCDFile[MAXPATH];  

  

Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);  

if (Status != NOERROR)  

    return Status;  

  

/\*  Add text... \*/  

  

Status = CompoundTextClose(hCompound,  

                           &hReturnCD,  

                           &dwReturnCDSize,  

                           achReturnCDFile,  

                           (sizeof achReturnCDFile)-1);  

if (Status != NOERROR)  

    {  

    CompoundTextDiscard(hCompound);  

    return Status;  

    }  

  




/\*  Process the data,
then clean up. \*/  

if (hReturnCD != NULLHANDLE)  

    {  

    /\*  Do something with data in a buffer... \*/  

  




     /\*  ... then free
the buffer \*/  

    OSMemFree(hReturnCD);  

    }  

else  

    {  

    /\*  Do something with data in a file... \*/  

  




     /\*  ... then
delete the temp. file \*/


     remove
(achReturnCDFile);  

    }


 **See Also :**


**[CompoundTextCreate](CompoundTextCreate.md)**


**[CompoundTextDiscard](CompoundTextDiscard.md)**



----------------------------------------------------------------------------------------------------------


 





