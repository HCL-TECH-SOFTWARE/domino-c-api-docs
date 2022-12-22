




<!--
 /\* Font Definitions \*/
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




**Initial Release 8.0.1**



**Function : encryption**



**NSFNoteCipherExtractFile** **- Extract a
file from an item in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCipherExtractFile(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhItem,  

      DWORD  ExtractFlags,  

      CIPHERHANDLE  hDecryptionCipher,  

      const char far \*FileName,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



Creates a
disk file from the contents of an attached item (referenced by its BLOCKID). 
The BLOCKID can be easily obtained by item name using NSFItemInfo.  The FileName
parameter specifies the path, file name, and extension of the file to be
created.  If only a file name and extension are supplied, the file will be
created in the current working directory.


      


      This
function supports new cryptographic keys and algorithms introduced in Release
8.0.1 as well as any from releases prior to 8.0.1.  Thus it is preferred over
the functions NSFNoteExtractFile and NSFNoteExtractFileExt in cases where their
ENCRYPTION\_KEY argument is non-NULL.


 


**Parameters :**



Input :  

hNote  -  Handle of note from which disk file will be extracted.  

  

bhItem  -  BLOCKID of the attachment item from which file is to be extracted.  

  

ExtractFlags  -  The possible values for the ExtractFlags are defined by the
NTEXT\_xxx symbols.  

  

hDecryptionCipher  -  Use NULLCIPHERHANDLE if the attachment is not encrypted,
or if it has already been decrypted by using a note decryption function with
the DECRYPT\_ATTACHMENTS\_IN\_PLACE flag.  Otherwise, use a CIPHERHANDLE returned
by NSFNoteCipherDecrypt.  

  

FileName  -  A null-terminated file name of the file that will be created.  

  

Reserved  -  Reserved, must be 0.  

  

pReserved  -  Reserved, must be NULL.  

  




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


STATUS                       error;



DBHANDLE                         hDb;


NOTEHANDLE
   hnote, hnote1;


char                                      server[100],
serverdb[100];


BLOCKID
retbid;


CIPHERHANDLE
rethCipherAttachments;


char
filepath[\_MAX\_PATH];


strcpy(localdb,
"extracttest.nsf");


 


........


 


error
= NSFNoteCreate(hDb, &hnote);


               


#ifdef
W32


               \_getcwd(filepath,
\_MAX\_PATH);


#ifdef
UNIX


               strcpy(filepath,
getenv("PWD"));


#endif


#endif     


                              


 


error
= NSFNoteAttachFile(hnote, ITEM\_NAME\_ATTACHMENT,


                                             strlen(ITEM\_NAME\_ATTACHMENT),filepath,"readme.txt",


                                             COMPRESS\_HUFF);


error
= NSFNoteUpdate(hnote, UPDATE\_FORCE);                    


error
= NSFNoteHasObjects(hnote, &retbid);


error
= NSFNoteCopyAndEncrypt(hnote, ENCRYPT\_WITH\_USER\_PUBLIC\_KEY, 


                                                            &hnote1);              


error
= OSMemoryAllocate(0, MAXONESEGSIZE, &rethCipherAttachments);


error
= NSFNoteCipherDecrypt(hnote1, NULLKFHANDLE, 0, &rethCipherAttachments, 0,
NULL);


error
= NSFNoteCipherExtractFile(hnote1, retbid, 0, rethCipherAttachments,
"out.txt",0, NULL);


error
= NSFCipherDestroy(&rethCipherAttachments)) 


remove("out.txt");


NSFNoteClose(hnote);


NSFNoteClose(hnote1);


NSFDbClose(hDb);


 **See Also :**


**[NSFCipherDestroy](NSFCipherDestroy.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteCopyAndEncrypt](NSFNoteCopyAndEncrypt.md)**



----------------------------------------------------------------------------------------------------------


 





