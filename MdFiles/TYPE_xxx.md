




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




 


**Symbolic Value : Field**



**TYPE\_xxx** **-** Item Data
Type definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      TYPE\_ERROR         -  (Computable; Host form)  

  

      TYPE\_UNAVAILABLE           -  (Computable; Host form)  

  

      TYPE\_TEXT             -  Standard text field. A field of TYPE\_TEXT is
stored as an array of characters without a null terminator. (Computable; Host
form)  

  

      TYPE\_TEXT\_LIST    -  A text list. A field of TYPE\_TEXT\_LIST consists of a
LIST structure which specifies the number of items in the list, followed by an
array in which each element contains the length of each item in the list,
followed by a packed character array with the text of the items. The text items
are packed into the array without null terminators. (Computable; Host form)  

  

      TYPE\_NUMBER       -  A number. A field of TYPE\_NUMBER is stored using the
C type double. (Computable; Host form)  

  

      TYPE\_NUMBER\_RANGE     -  A list of numbers. A field of TYPE\_NUMBER\_RANGE
consists of a RANGE structure (which contains the number of items in the list)
followed by a sequence of NUMBER structures. Number ranges are not currently
supported by Domino. Therefore, the RangeEntries field of the RANGE structure
should always be zero with fields of TYPE\_NUMBER\_RANGE. (Computable; Host form)  

  

      TYPE\_TIME             -  A date/time field. A field of TYPE\_TIME is
stored in the Domino binary time/date format. (Computable; Host form)  

  

      TYPE\_TIME\_RANGE            -  A list of date/times and/or a list of
date/time ranges. A field of TYPE\_TIME\_RANGE consist of a RANGE structure (which
contains the number of items in the list, followed by the number of items
specified as ranges), followed by a sequence of TIMEDATE structures, followed
by a sequence of TIMEDATE\_PAIR structures. (Computable; Host form)  

  

      TYPE\_FORMULA     -  A $FORMULA item in a view note. A field of
TYPE\_FORMULA is the $FORMULA item in a view note. It consists of the compiled
view selection formula and the compiled column formulas, with the appropriate
summary items set. See the descriptions of the functions NSFFormulaCompile(),
NSFFormulaSummaryItem(), and NSFFormulaMerge() for more details. (Computable;
Host form)  

  

      TYPE\_USERID         -  A Notes V1/V2 Author field: user name and license
ID. A field of TYPE\_USERID is a Notes V1/V2 Author field. It consists of a text
user name and optional server names in parenthesis, followed by an 8 byte
license ID. This type is obsolete in Notes 3.0 or later. See Data Type : Item
(Field) Information : Author Names for the Notes 3.0 or later format for
document author fields. (Computable; Host form)  

  

      TYPE\_INVALID\_OR\_UNKNOWN      -  Returned by NSFItemInfo in the argument
"value\_datatype" when NSFItemInfo is not able to find an item.
(Non-Computable; Host form)  

  

      TYPE\_COMPOSITE             -  Rich text. A field of TYPE\_COMPOSITE is a
rich text field. A rich text field may contain many types of objects, including
text, tables, document links, pictures, and DDE links. >64K handled by more
than one item of same name concatenated. (See Rich Text datatypes).
(Non-Computable; Canonical form)  

  

      TYPE\_COLLATION   -  A $COLLATION item in a view note. A field of
TYPE\_COLLATION is the $COLLATION item in a view note, which describes how data
is sorted in each column in the view. (Non-Computable; Canonical form)  

  

      TYPE\_OBJECT        -  (Non-Computable; Canonical form)  

  

      TYPE\_NOTEREF\_LIST        -  A $REF (Response Reference List) item. A
field of TYPE\_NOTEREF\_LIST is a Response Reference List. All response documents
contain a Response Reference List item, which indicates that the document is a
response note. A Response Reference List item has field name "$REF".
The Response Reference consists of a LIST header structure, followed by the
UNIVERSALNOTEID of the parent document. (Non-Computable; Host form)  

  

      TYPE\_VIEW\_FORMAT         -  A $VIEWFORMAT item in a view note. A field of
TYPE\_VIEW\_FORMAT is the $VIEWFORMAT item in a view note, which defines the
format of a view. It consists of a VIEW\_TABLE\_FORMAT structure, followed by a
sequence of VIEW\_COLUMN\_FORMAT structures (one for each column in the view),
followed by a VIEW\_TABLE\_FORMAT2 structure. See the descriptions of these
structures for more details. (Non-Computable; Canonical form)  

  

      TYPE\_ICON             -  (Non-Computable; Canonical form)  

  

      TYPE\_NOTELINK\_LIST        -  A $Links (Doc Link Reference List) item. A
field of TYPE\_NOTELINK\_LIST is a Doc Link Reference List. Domino and Notes
append a DocLink Reference List item to documents that contain Doc Links. A
DocLink Reference Item has field name "$Links". A DocLink Reference
List consists of a LIST header structure, followed by an array of NOTELINK structures.
(Non-Computable; Host form)  

  

      TYPE\_SIGNATURE   -  (Non-Computable; Canonical form)  

  

      TYPE\_SEAL             -  (Non-Computable; Canonical form)  

  

      TYPE\_SEALDATA    -  (Non-Computable; Canonical form)  

  

      TYPE\_SEAL\_LIST    -  (Non-Computable; Canonical form)  

  

      TYPE\_HIGHLIGHTS             -  (Non-Computable; Host form)  

  

      TYPE\_WORKSHEET\_DATA             -  Used ONLY by Chronicle product.
(Non-Computable; Canonical form)  

  

      TYPE\_USERDATA   -  Arbitrary format data. (Non-Computable; Canonical
form)  

  

      TYPE\_QUERY          -  Saved query CD records. (Non-Computable; Canonical
form)  

  

      TYPE\_ACTION         -  Saved action CD records. (Non-Computable;
Canonical form)  

  

      TYPE\_ASSISTANT\_INFO     -  Saved assistant info. (Non-Computable;
Canonical form)  

  

      TYPE\_VIEWMAP\_DATASET            -  Saved ViewMap dataset (Non-Computable;
Canonical form)  

  

      TYPE\_VIEWMAP\_LAYOUT   -  Saved ViewMap layout. (Non-Computable; Canonical
form)  

  

      TYPE\_LSOBJECT    -  Saved LotusScript Object code for an agent.  

  

      TYPE\_HTML            -  LMBCS-encoded HTML, >64K handled by more than
one item of same name concatenated.  

  

      TYPE\_SCHED\_LIST             -  Busy time schedule entries list.
(Non-computable; Host form)  

  

      TYPE\_CALENDAR\_FORMAT           -  (Non-Computable; Canonical form)  

  

      TYPE\_MIME\_PART   -  MIME body part; Canonical form  

  

      TYPE\_RFC822\_TEXT           -  RFC822( RFC2047) message header; Canonical
form  

  




**Description :**



These values
define the datatype of an item (field) in a note.  

  

All datatypes below are passed to NSF in either host (machine-specific byte
ordering and padding) or canonical form (Intel 86 packed form).  The format of
each datatype, as it is passed to and from NSF functions, is listed below in
the comment field next to each of the data types.  (This host/canonical issue
is NOT applicable to Intel86 machines, because on that machine, they are the
same and no conversion is required).  On all other machines, use the ODS
subroutine package to perform conversions of those datatypes in canonical
format before they can be interpreted.  

  

Here is the format of the various LIST data types:  

  

TYPE\_TEXT\_LIST:  

    LIST /\* list header \*/  

    USHORT ... /\* array of text string lengths following \*/  

    text /\* now comes the packed text for all strings \*/  

  

TYPE\_NUMBER\_RANGE:  

    RANGE /\* range header \*/  

    NUMBER ... /\* array of NUMBERs \*/  

    NUMBER\_PAIR ... /\* array of NUMBER\_PAIRs \*/  

  

TYPE\_TIME\_RANGE:  

    RANGE /\* range header \*/  

    TIMEDATE ... /\* array of time/date's \*/  

    TIMEDATE\_PAIR ... /\* array of time/date pairs \*/  

  

TYPE\_NOTEREF\_LIST:  

    LIST /\* list header \*/  

    UNIVERSALNOTEID /\* array of UNIVERSALNOTEIDs \*/  

  

TYPE\_NOTELINK\_LIST:  

    LIST /\* list header \*/  

    NOTELINK ... /\* array of NOTELINKs \*/  

   

TYPE\_USERDATA:  

    BYTE Length /\* length of LMBCS "format-name" string \*/  

    char[Length]; /\* LMBCS "format-name" string used to distinguish
various formats of user  

                                  data that follows. ("format-name"
string is NOT NULL-TERMINATED!) \*/  

    data /\* next is variable-length data that corresponds to the format
specified by the string \*/


 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**



----------------------------------------------------------------------------------------------------------


 





