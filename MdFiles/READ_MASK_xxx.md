




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Views; Folders**



**READ\_MASK\_xxx** **-** Information
returned by NIFReadEntries.


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      READ\_MASK\_NOTEID         -  NOTEID of note  

  

      READ\_MASK\_NOTEUNID    -  UNID of note.  

  

      READ\_MASK\_NOTECLASS              -  Note class of note. Occupies one WORD
in the buffer.  

  

      READ\_MASK\_INDEXSIBLINGS        -  Number of siblings in view or folder.
Occupies one DWORD in the buffer.  

  

      READ\_MASK\_INDEXCHILDREN       -  Number of immediate children in view or
folder. Subcategories are included in the count. Occupies one DWORD in the
buffer.  

  

      READ\_MASK\_INDEXDESCENDANTS          -  Number of descendents in view or
folder. Subcategories are not included in the count. Occupies one DWORD in the
buffer.  

  

      READ\_MASK\_INDEXANYUNREAD   -  TRUE if unread (or any descendents unread),
FALSE otherwise. Occupies one WORD in the buffer.  

  

      READ\_MASK\_INDENTLEVELS         -  Number of levels that this entry should
be indented in a formatted view or folder. Occupies one WORD in the buffer.  

  

      READ\_MASK\_SCORE          -  Relevancy score of an entry. Occupies one
WORD in the buffer. FTSearch must be called prior to NIFReadEntries. The
FT\_SEARCH\_SET\_COLL search option or'd with the FT\_SEARCH\_SCORES search option
must be specified in the call to FTSearch.  

  

      READ\_MASK\_INDEXUNREAD          -  TRUE if this entry is unread, FALSE
otherwise. Occupies one WORD in the buffer.  

  

      READ\_MASK\_COLLECTIONSTATS             -  Collection statistics (as a
COLLECTIONSTATS structure).  

  

      READ\_MASK\_INDEXPOSITION       -  Truncated COLLECTIONPOSITION. Use
COLLECTIONPOSITIONSIZE macro to determine the size it occupies in the buffer.  

  

      READ\_MASK\_SUMMARYVALUES    -  Summary buffer of summary data values that
appear in the view. The data is in the format of an ITEM\_VALUE\_TABLE. This
format consists of an ITEM\_VALUE\_TABLE followed by an array of WORD values
containing the lengths, in bytes, of the data items; there is one WORD for each
item in the table. The data length table is followed, in turn, by a packed
sequence of item values. Each item value includes the item's datatype. The
item's datatype is stored in the first USHORT of each item value.  

  

      READ\_MASK\_SUMMARY     -  Summary buffer of summary data values that
appear in the view. The data is in the format of an ITEM\_TABLE. This format
consists of an ITEM\_TABLE structure, followed by an array of ITEM structures,
followed by packed pairs, where each pair consists of the item name followed by
the item value. Each item value includes the item's datatype. The item's
datatype is stored in the first USHORT of each item value.  

  




**Description :**



These flags
control what information is returned by NIFReadEntries for each note that is
found. All of the information requested is returned in the buffer that
NIFReadEntries creates.  

  

The return buffer consists of:  

  

1) The COLLECTIONSTATS structure, if requested by READ\_MASK\_COLLECTIONSTATS.
This structure is returned only once at the beginning of the buffer, and is not
repeated for each note.  

  

2) Information about each note. Each flag requests a different bit of
information about the note.  If more than one flag is defined, the values
follow each other, in the order in which the bits are listed here.  This
portion repeats for as many notes as are found.


 **See Also :**


**[ITEM\_TABLE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B43006B5125)**


**[ITEM\_VALUE\_TABLE](ITEM_VALUE_TABLE.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





