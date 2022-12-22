




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.0**



**Function : Note**



**NSFNoteComputeWithForm** **- Validate
the note against the form.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteComputeWithForm(**  

      NOTEHANDLE  hNote,  

      NOTEHANDLE  hFormNote,  

      DWORD  dwFlags,  

      CWF\_ERROR\_PROC  ErrorRoutine,  

      void \*CallersContext**);**



**Description :**



Given a
handle to an open note and a handle to an open form note, for each field
defined in the form, this function will:


 


1)  Validate
fields with Default Value formulas,


 


2)  Validate
fields with Translation formulas,


 


3)  Validate
fields with Validation formulas,


 


4) 
Calculate values for Computed fields.


 


If no error
callback routine is supplied and the flag CWF\_CONTINUE\_ON\_ERROR is not set (in
the dwFlags argument), if one of the validation formulas fails, an error is
returned.  If the CWF\_CONTINUE\_ON\_ERROR flag is set, the error is not returned.


 


If a pointer
to an error callback routine is supplied and one of the validation formulas
fails, the error callback routine is called.  The argument CallersContext is
passed directly to the error callback.  For the calling sequence and arguments,
see the data type CWF\_ERROR\_PROC.  If the CWF\_CONTINUE\_ON\_ERROR flag is set,
error processing for the field is skipped;  if a pointer to a callback function
is supplied, the callback function will be ignored.


 


**Parameters :**



Input :  

hNote  -  Handle to the note to be validated.  

  

hFormNote  -  Handle to the form note.   If NULLHANDLE is specified, then the
function will use the note's embedded form; if there is no embedded form, it
will use the form specified in the form field; if there is no form field, this
function will use the default database form.  

  

dwFlags  -  Validation flags.  For the values supported, see the symbolic value
CWF\_xxx.  

  

ErrorRoutine  -  Pointer to the error callback routine.  

  

CallersContext  -  Context information to pass to the error callback routine. 
This 32-bit value is passed unchanged to the callback.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


...


 


/\* Create a
note and add all input data to it. \*/  

    if (error = NSFNoteCreate (db\_handle, &note\_handle))  

    {  

        NSFDbClose (db\_handle);  

        API\_RETURN (ERR(error));  

    }


 


/\* Prompt
for input data. \*/  

    PromptValues(&length, &width);


 


/\* Set the
input data measurement \*/  

    temp\_val = (NUMBER) length;  

    if (error = NSFItemSetNumber (note\_handle, "Length",
&temp\_val))  

        goto Item\_Error;


 


   
temp\_val = (NUMBER) width;  

    if (error = NSFItemSetNumber (note\_handle, "Width",
&temp\_val))  

        goto Item\_Error;


 


/\* Call
NSFNoteComputeWithForm to   

 \* 1) ensure that input measurement data is valid, or flag error in callback  

 \* 2) compute the output measurement data, or flag error in callback  

 \*/  

    if (error = NSFNoteComputeWithForm (note\_handle, NULLHANDLE, (DWORD) 0,  

                                        CWFCallback, NULL))  

        goto Item\_Error;


 


/\* No
error; get entered and computed field values and display measurement summary \*/  

    if (NSFItemGetNumber (note\_handle, "Length", &length) ==
FALSE)  

        goto Item\_Error;  

    if (NSFItemGetNumber (note\_handle, "Width", &width) == FALSE)  

        goto Item\_Error;  

    if (NSFItemGetNumber (note\_handle, "Perimeter", &perimeter)
== FALSE)  

        goto Item\_Error;  

    if (NSFItemGetNumber (note\_handle, "Area", &area) == FALSE)  

        goto Item\_Error;  

    DisplayValues(length, width, perimeter, area);


 


/\* Update
the note. \*/  

    if (error = NSFNoteUpdate (note\_handle, 0))  

        goto Item\_Error;


 


...


 **See Also :**


**[CWF\_ERROR\_PROC](CWF_ERROR_PROC.md)**


**[CWF\_xxx (Return Codes)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70D2C510DEF69C6C85256261005D9C2B)**


**[CWF\_xxx (Validation Phases)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E2F5A18E435B5FE985256237005182EE)**



----------------------------------------------------------------------------------------------------------


 





