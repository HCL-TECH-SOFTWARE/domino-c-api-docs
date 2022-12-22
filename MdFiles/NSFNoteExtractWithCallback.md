




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




**Initial Release 6**



**Function : File Attachment**



**NSFNoteExtractWithCallback** **- Extract a
file with a user defined call back function.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteExtractWithCallback(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhItem,  

      ENCRYPTION\_KEY far \*DecryptionKey,  

      WORD  wFlags,  

      NOTEEXTRACTCALLBACK  pNoteExtractCallback,  

      void far \*pParam**);**



**Description :**



This
function allows flexibility with file attachments.  It may be desirable to read
through file attachment data without having to save the file to disk.  The user
defined call back function will be called however many times necessary with a
pointer to the file data and the number of bytes returned.  The user has the
option with the call back function to do what is desired with the attachment
data.


 


   **Note: NSFNoteExtractWithCallback
should be deprecated from Notes/Domino 8.0.1. The preferred function to use in
their place is NSFNoteCipherDecrypt.**



**Parameters :**



Input :  

hNote  -  Handle of note with a file attachment.  

  

bhItem  -  BLOCKID of the attachment item from which file is to be extracted. 
The BLOCKID can be easily obtained by item name using NSFItemInfo.  

  

DecryptionKey  -  Use NULL if the attachment is not encrypted.  Otherwise, use
a pointer to the ENCRYPTION\_KEY structure returned by NSFNoteDecrypt.  

  

wFlags  -  The possible values for the wFlags are defined by the NTEXT\_xxx
symbol.  

  

pNoteExtractCallback  -  A pointer to the user defined Call back function.    

  

pParam  -  user defined parameter passed to the user defined call back routine
NOTEEXTRACTWITHCALLBACK.  This data can be a means for keeping track of
information during the process of extracting an attached file.  For example a
structure can be defined that can keep track of the amount of data extracted
and information on the extracted file if the extracted data is to be written to
a file.  

  




Output :  

(routine)  -  Return status from this call includes:  

  

NOERROR - Successfully extracted file.  

  

ERR\_ENCODING - Unknown type of compression technique.  

  

ERR\_NOEXTRACT\_ENCRYPTED - You must supply the decryption key in order to
extract this file.  

  

ERR\_NOTE\_BADATTSIGN - Attachment has been modified or corrupted since signed!  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


/\* Open the note. \*/


 


    if
(error = NSFNoteOpen (


           
\*(DBHANDLE\*)db\_handle,  /\* database handle \*/


           
SearchMatch.ID.NoteID,  /\* note ID \*/


           
0,                      /\* open flags \*/


           
&note\_handle))          /\* note handle (return) \*/


 


       
return (error);


 


/\* Look for
the File attachment for this note. This function tells us


whether the
field is there, and if present, its location (BLOCKID)


within
Domino and Notes' memory. Check the return code for "field not found"
versus


a real
error. \*/


 


    error =
NSFItemInfo (


           
note\_handle,        /\* note handle \*/


            "$FILE",       
/\* field we want \*/


           
(WORD)strlen("$FILE"),    /\* length of above \*/


           
&bkItem,            /\* full field (return) \*/


           
&field\_type,        /\* field type (return) \*/


           
&field\_block,        /\* field contents (return) \*/


           
&field\_length);        /\* field length (return) \*/


 


    if
(ERR(error) == NOERROR)


       
field\_found = TRUE;


 


    if
(ERR(error) == ERR\_ITEM\_NOT\_FOUND)


    {


       
field\_found = FALSE;


       
error = NOERROR;


    }


 


    if
(error)


    {


       
NSFNoteClose (note\_handle);


       
return (error);


    }


 


/\* If the
RICH\_TEXT field is there, do the next few sections of code. \*/


        memset(&pParam,
0, sizeof(pParam));


    if
(field\_found)


    {


        /\*


        \*
Call ExtractWithCallback for how ever many times to read through the file
attachment data


        \*/     


        if(error
= NSFNoteExtractWithCallback(note\_handle, bkItem, NULL, 0, ExtractWithCallback,
&pParam))


        {


               NSFNoteClose(note\_handle);


               return(error);


        }


    }


        /\*
If the $FILE field is not there, print a message. \*/


    else


       
printf ("\n$FILE(file attachment) field not found.\n");


 


        /\*
Close the file handle if opened to write data \*/


        if(pParam.pOutputFile)


               CloseHandle(pParam.pOutputFile);


 


/\* Close
the note. \*/


 


    if
(error = NSFNoteClose (note\_handle))


       
return (error);


 


/\* End of
subroutine. \*/


 


    return
(NOERROR);


 


}


 


/\*


 \* User
defined call back function to read through the file attachment data.  In this


 \* case the
file attachment data will be written to a file.


 \*/


STATUS
LNCALLBACK ExtractWithCallback(const BYTE \*bytes, DWORD length, void far
\*pParam)


{


        struct
CallBackData \*tmpCtx = (struct CallBackData\*)pParam;


        DWORD
numberWritten = 0;


        STATUS
err = NOERROR;


 


        /\*
Check to see if first time through \*/


        if(!tmpCtx->pOutputFile)


        {


               /\*
Open the file to write the exported data \*/


               tmpCtx->pOutputFile
= CreateFile("FileData.Txt",


                       GENERIC\_WRITE|GENERIC\_READ,FILE\_SHARE\_READ
| FILE\_SHARE\_WRITE,


                       NULL,
CREATE\_ALWAYS,FILE\_ATTRIBUTE\_NORMAL,NULL);


               if
(!tmpCtx->pOutputFile)


               {


                       printf("Error: 
Unable to open output file:%s.\n", "FileData.Txt");


                       goto
Exit0;


               }


               tmpCtx->totalBytesWritten
= 0;


        }


        err
= WriteFile(tmpCtx->pOutputFile, bytes, length, &numberWritten, NULL);


        if(err
== 1)


               err
= NOERROR;


        printf("\nBytesWritten
= %s\n",bytes);


        if(
numberWritten != length )


        {


               printf("Error:
Did not write specified bytes required %d\n", length );


               goto
Exit0;


        }


        else


               tmpCtx->totalBytesWritten
+= numberWritten;


 


Exit0:


        return(err);


}


 **See Also :**


**[NOTEEXTRACTCALLBACK](NOTEEXTRACTCALLBACK.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteDecrypt](NSFNoteDecrypt.md)**


**[NSFNoteDetachFile](NSFNoteDetachFile.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**



----------------------------------------------------------------------------------------------------------


 





