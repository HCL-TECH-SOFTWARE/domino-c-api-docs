




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



**TYPE\_xxx [NOTELINK\_LIST]** **-** Item Data
Type - DocLink Reference List


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



Domino and
Notes append a DocLink Reference List item to documents that contain Doc
Links.  A DocLink Reference Item has field name "$Links".  The
internal (API level) data type is TYPE\_NOTELINK\_LIST. Domino and Notes use the
DocLink Reference List to resolve Doc Links in the rich text field.  

  

A DocLink Reference List item consists of a LIST header structure, followed by
an array of NOTELINK structures, as follows:  

LIST  

NOTELINK  

NOTELINK  

...  

  

  

The LIST header identifies how many NOTELINK structures follow. The list
contains one entry for every CDLINK2 record in the document.  

Doc Links created from the Notes user interface have two parts: a CDLINK2
record, and a DocLink Reference.  The CDLINK2 record resides in the rich text
field. The DocLink Reference resides in the DocLink Reference List.   

  

A CDLINK2 record consists of a header followed by an index. The index in the
CDLINK2 identifies one of the NOTELINK  entries in the DocLink Reference List.  

  

The header of a CDLINK2 is a WSIG and the index is a WORD.  

  

A NOTELINK contains all the information necessary to open a specific document
from any database or server. When a user launches a Doc Link by double-clicking
on the icon in the rich text field, Domino and Notes use the index in the
CDLINK2 structure to get the corresponding NOTELINK from the DocLink Reference
List.   

  

There are two types of DocLinks. The first type consists of a CDLINK2 record
and a DocLink Reference.  The second type consists of a CDLINKEXPORT2 record.   

  

When a user initially creates a Doc Link in a document, the result is the first
type of Doc Link.  However, when a user copies a DocLink from a rich text field
to the clipboard, Domino and Notes convert the CDLINK2 structure to a
CDLINKEXPORT2 structure in the data that is copied to the clipboard. If this
clipboard data is pasted into the rich text field of another Domino document,
the resulting Doc Link is the second type of Doc Link.


 **Sample Usage :**


/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  

  

    FUNCTION:   DumpNotelinkList  

  

    A NOTELINK List is a LIST followed by an array of NOTELINK structures.  

  

    A NOTELINK structure universally (across all servers) describes  

    a note LINK:  

                typedef struct   

                {  

                    TIMEDATE File;  

                    UNID View;  

                    UNID Note;  

                } NOTELINK;  

  

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/  

  

void  LNPUBLIC  DumpNotelinkList (PCHAR pData, WORD length)  

{  

    LIST        List;  

    USHORT      ListEntries, i;  

    NOTELINK   \*pNoteLink;  

    TIMEDATE    tdFile ;     

    UNID        unidView;  

     UNID        unidNote;  

  

    List = \*((LIST\*)pData);  

    ListEntries = List.ListEntries;  

    ((LIST\*)pData)++;  

    fprintf (dumpfile, "\tlist has %d NOTELINKs\n", ListEntries);  

  

    for (i = 0; i<ListEntries; i++,((NOTELINK \*)pData)++)  

    {  

        fprintf (dumpfile, "\tNotelink #%d:\n", i+1);  

        pNoteLink = (NOTELINK \*)pData;  

        tdFile = pNoteLink->File;  

        unidView = pNoteLink->View;  

        unidNote = pNoteLink->Note;  

        fprintf (dumpfile, "\t Database replica ID = %#.4lx -
%#.4lx\n",   

                    tdFile.Innards[1],  

                    tdFile.Innards[0]);  

        fprintf (dumpfile, "\t View UNID.File = %#.4lx - %#.4lx\n",  

                    unidView.File.Innards[1],  

                    unidView.File.Innards[0]);  

        fprintf (dumpfile, "\t View UNID.Note = %#.4lx - %#.4lx\n",  

                    unidView.Note.Innards[1],  

                    unidView.Note.Innards[0]);  

        fprintf (dumpfile, "\t Note UNID.File = %#.4lx - %#.4lx\n",  

                    unidNote.File.Innards[1],  

                    unidNote.File.Innards[0]);  

        fprintf (dumpfile, "\t Note UNID.Note = %#.4lx - %#.4lx\n",  

                    unidNote.Note.Innards[1],  

                    unidNote.Note.Innards[0]);  

    }  

  

    return;  

}


 **See Also :**


**[CDLINK2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00A50061002B004585255E7D0081902C)**


**[CDLINKEXPORT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255D2800785F80)**


**[LIST](LIST.md)**


**[NOTELINK](NOTELINK.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**


**[TYPE\_xxx [NOTEREF\_LIST]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7D9F05D89E5500B28525622E0063378C)**



----------------------------------------------------------------------------------------------------------


 





