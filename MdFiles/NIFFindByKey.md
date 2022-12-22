




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




 


**Function : Views; Folders**



**NIFFindByKey** **- Finds
notes using single or multiple sort keys.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



STATUS
LNPUBLIC **NIFFindByKey(**  

      HCOLLECTION  hCollection,  

      void far \*KeyBuffer,  

      WORD  FindFlags,  

      COLLECTIONPOSITION far \*retIndexPos,  

      DWORD far \*retNumMatches**);**



**Description :**



This
function searches through a collection for the first note whose sort column
values match the given search keys.  The search key consists of a buffer
containing one or several values structured as an ITEM\_TABLE. This function
matches each value in the search key against the corresponding sorted column of
the view or folder. Only sorted columns are used. The values in the search key
item table must be specified in the same order as the sorted columns in the
view or folder, from left to right.  Other unsorted columns may lie between the
sorted columns to be searched.  For example, suppose view columns 1, 3, 4 and 5
are sorted.  The key buffer may contain search keys for: just column 1; columns
1 and 3; or for columns 1, 3, and 4.  

  

This function yields the COLLECTIONPOSITION of the first note in the collection
that matches the keys. It also yields a count of the number of notes that match
the keys. Since all notes that match the keys appear contiguously in the view
or folder, you may pass the resulting COLLECTIONPOSITION and match count as
inputs to NIFReadEntries to read all the entries in the collection that match
the keys.


 


If multiple
notes match the specified (partial) keys, and FIND\_FIRST\_EQUAL (the default
flag) is specified, then the position of the first matching note is returned
("first" is defined by the note which collates before all the others
in the view).  The position of the last matching note is returned if
FIND\_LAST\_EQUAL is specified.  If FIND\_LESS\_THAN is specified, then the last
note with a key value less than the specified key is returned.  If
FIND\_GREATER\_THAN is specified, then the first note with a key value greater
than the specified key is returned.  

  

This routine cannot be used to locate notes that are categorized under multiple
categories (the resulting position is unpredictable), and also cannot be used
to locate responses.  

  

This routine is usually not appropriate for equality searches of key values of
TYPE\_TIME.  A match will only be found if the key value is as precise as and is
equal to the internally stored data.  TYPE\_TIME data is displayed with less
precision than what is stored internally.  Use inequality searches, such as
FIND\_GREATER\_THAN or FIND\_LESS\_THAN, for TYPE\_TIME key values to avoid having
to find an exact match of the specified value.  If the precise key value is
known, however, equality searches of TYPE\_TIME values are supported.


 


Returning
the number of matches on an inequality search is not supported.  In other
words, if you specify any one of the following for the FindFlags argument:


      FIND\_LESS\_THAN


      FIND\_LESS\_THAN
| FIND\_EQUAL


      FIND\_GREATER\_THAN


      FIND\_GREATER\_THAN
| FIND\_EQUAL


this
function cannot determine the number of notes that match the search condition. 
In this case you may want to specify NULL for the retNumMatches argument.  If
you do not specify NULL for the retNumMatches argument, then \*retNumMatches
will be set to 1.


 


**Parameters :**



Input :  

hCollection  -  The handle of the collection you want to search.  

  

KeyBuffer  -  A pointer to a Domino memory object containing an ITEM\_TABLE and
its accompanying array of ITEMs.  The ITEMs must be specified in the same order
as the sorted columns of the view or folder.  The ITEM's  '.NameLength' value
may be set to zero and the ITEM's name may be omitted from the information
following the ITEM header.  If the ITEM's name and NameLength values are
specified, they are ignored by this function.  Each ITEM must match the data
type of the information in the corresponding sorted column.   

  

FindFlags  -  Flags that control the comparison rules used when a key is
compared to the notes in the collection. The find flags are described in
FIND\_xxx, and may be OR'ed together to combine functionailty.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_NOT\_FOUND  

  

  

retIndexPos  -  The address of a COLLECTIONPOSITION in which the position
within the collection where the match is found is returned. The exact position
that is returned depends on the value of the FIND\_FLAGS that are specified.  If
more than one matching note was found, the position of the first matching note
will be returned.  You can use retIndexPos with NIFReadEntries to get the notes
found by this search.  

  

retNumMatches  -  The address of a DWORD in which the number of matching notes
is returned.  This value is usually passed-on to a subsequent call to
NIFReadEntries().  It can also be used simply to determine if the name has
multiple matches or not (ambiguity).    

  

The number of matching entries is not supported if FIND\_LESS\_THAN,
FIND\_LESS\_THAN | FIND\_EQUAL, FIND\_GREATER\_THAN, or FIND\_GREATER\_THAN | FIND\_EQUAL
is specified in the FindFlags argument.  In this case, you may specify NULL for
the retNumMatches argument.  If you do not specify NULL, then 1 is returned as
the number of matching notes.  

  




 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFReadEntries](NIFReadEntries.md)**


**[ITEM\_TABLE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B43006B5125)**



----------------------------------------------------------------------------------------------------------


 





