




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




 


**Symbolic Value : Item (Field)
Information**



**TYPE\_xxx [NOTEREF\_LIST]** **-** Item Data
Type - Response Reference List


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



All response
documents contain a Response Reference List item.  This item has field name
"$REF" and data type TYPE\_NOTEREF\_LIST. The response reference list
item identifies the main, or parent document.   

  

A response reference list item consists of a LIST header structure, followed
by  the UNIVERSALNOTEID (UNID) of the parent document, as follows:  

LIST  

UNIVERSALNOTEID  

  

To create a response document in a Domino database, first obtain the UNID of
the parent document. Open or create the note that will be the response note.
Then initialize a buffer that consists of a LIST structure followed by the UNID
of the parent. Call NSFItemAppend to append this buffer to the note. Use the
symbolic constant FIELD\_LINK (defined as "$REF") to specify the field
name. Specify data type TYPE\_NOTEREF\_LIST.  

  

Domino and Notes automatically convert items of type TYPE\_NOTEREF\_LIST to
canonical format when appending them to a note, and convert them to host format
when reading them from a note. Therefore, do not perform host/canonical
conversion on this data.


 **Sample Usage :**


STATUS LNPUBLIC
AppendRefItem( NOTEHANDLE hRespNote, OID oidMainNote)  

{


    STATUS      error =
NOERROR;  

   DWORD       dwValueLen;  

   char       \*buf;  

   LIST       ListHdr;  

   UNID       NoteUNID;


 


   
dwValueLen = sizeof(LIST) + sizeof(UNID);


 


    buf = 
(char \*)malloc(sizeof(LIST) + sizeof(UNID));


    if (buf
== NULL)  

    {  

         printf ("Error: unable to allocate %lu bytes memory.\n",
dwValueLen);  

         return(ERR\_AUTH\_FLD\_MALLOC);  

    }


 


    /\*
Initialize the LIST header part of the response reference list \*/  

    ListHdr.ListEntries = (USHORT) 1;


 


    /\*
Initialize the UNID part of the response reference list \*/  

    NoteUNID.File = oidMainNote.File; /\* user-unique identifier \*/  

    NoteUNID.Note = oidMainNote.Note; /\* time/date when the note was created \*/


 


    /\* Pack
the LIST and the UNID members of the Noteref list into


       a
memory block.  

    \*/  

    memcpy(buf, (char\*)&ListHdr, sizeof(LIST));  

    memcpy((buf + sizeof(LIST)), (char\*)&NoteUNID, sizeof(UNID));


 


    if
(error = NSFItemAppend ( hRespNote,  

                                ITEM\_SUMMARY,  

                                FIELD\_LINK,             /\* "$REF" \*/  

                                strlen(FIELD\_LINK),  

                                TYPE\_NOTEREF\_LIST,      /\* $REF data type \*/  

                                buf,  

                                dwValueLen))  

    {  

        printf ("Error: unable to append Note Reference List to
Response.\n")  

    }


    free
(buf);  

    return (error);  

}


 


 **See Also :**


**[LIST](LIST.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**


**[NSFItemAppend](NSFItemAppend.md)**



----------------------------------------------------------------------------------------------------------


 





