




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




 


**Data Type : File Attachment**



**FILEOBJECT** **-** Structure of
a file object item ($FILE).


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   OBJECT\_DESCRIPTOR Header; /\* object header \*/  

   WORD FileNameLength;      /\* length of file name \*/  

   WORD HostType;            /\* text delimiters (HOST\_xxx) \*/  

   WORD CompressionType;     /\* compression used (COMPRESS\_xxx) \*/  

   WORD FileAttributes;      /\* orig. file attribs (ATTRIB\_xxx) \*/  

   WORD Flags;               /\* misc. flags (FILEFLAG\_xxx) \*/  

   DWORD FileSize;           /\* orig. file size \*/  

   TIMEDATE FileCreated;     /\* orig. file date/time of creation \*/  

   TIMEDATE FileModified;    /\* orig. file date/time of mod. \*/  

/\* Now comes the file name... It is the original RELATIVE file path  

                                with no device specifiers \*/  

} FILEOBJECT;


 


**Description :**



This is the
strucure of a file attachment item.  For each file attached to a note, an item
with field name "$FILE" (ITEM\_NAME\_ATTACHMENT) and data type TYPE\_OBJECT
is appended to the note.  The value of this item is a structure of type
FILEOBJECT.  Note that the data of the attached file is not stored in this
item. Rather, it is stored in an object identified by the RRV member of the
OBJECT\_DESCRIPTOR.  

  

For normal file attachments, you do not need to access the file attachment item
directly. Use the functions NSFNoteAttachFile, NSFNoteDetachFile, and
NSFNoteExtractFile to manipulate file attachments.  

  

If you do need to access items of type FILE\_OBJECT directly, and if your API
program runs on a non-Intel platform such as Unix, then you must convert the
item data from Domino canonical format to Host format before accessing members
of the FILEOBJECT structure.


 **Sample Usage :**


    OBJECT\_DESCRIPTOR 
\*pObject;  

    FILEOBJECT         \*pFileObject;  

    WORD                wFileNameLen;  

    BYTE               \*pFileNameStart;  

    WORD                wHostType;  

    CHAR               \*szHostType;  

    WORD                wCompress;  

    CHAR                szFileCreated[MAXALPHATIMEDATE+1];  

    CHAR                szFileModified[MAXALPHATIMEDATE+1];  

    CHAR               \*szFileName;  

    FILEOBJECT\_MACEXT  \*pMACFileObject;  

    FILEOBJECT\_HPFSEXT \*pHPFSFileObject;  

  

    /\* This code assumes non-Unix environment such as Windows.  

       On a Unix platform, for example, this code would need to be modified  

       to convert the OBJECT\_DESCRIPTOR structure from Domino canonical   

       format to host format.  

    \*/  

  

    pObject = (OBJECT\_DESCRIPTOR\*)pData;  

  

    if ( pObject->ObjectType != OBJECT\_FILE )  

    {  

        fprintf( dumpfile, "  Object Type = UNKNOWN (%#x).\n",   

                                                pObject->ObjectType );  

        return;  

    }  

    fprintf( dumpfile, "  Object Type = OBJECT\_FILE.\n" );  

  

    pFileObject = (FILEOBJECT\*)pData;  

  

    /\* get file name \*/  

    wFileNameLen = pFileObject->FileNameLength;  

    ((FILEOBJECT\*)pData)++ ;  

    pFileNameStart = (CHAR\*)pData;  

    szFileName = (CHAR\*)malloc(wFileNameLen+1);  

    memcpy( szFileName, pFileNameStart, wFileNameLen );  

    szFileName[wFileNameLen] = '\0';  

    fprintf( dumpfile, "  File Name = '%s'.\n", szFileName );  

    free(szFileName);  

  




 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteDetachFile](NSFNoteDetachFile.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**


**[ODSReadMemory](ODSReadMemory.md)**


**[\_xxx (ODS Types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6624318DA38E8A885255F18007069DE)**



----------------------------------------------------------------------------------------------------------


 





