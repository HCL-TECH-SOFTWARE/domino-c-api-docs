##### Symbolic Value : Field
##### TYPE_xxx - Item Data Type definitions.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	TYPE_ERROR	  -  (Computable; Host form)

	TYPE_UNAVAILABLE	  -  (Computable; Host form)

	TYPE_TEXT	  -  Standard text field. A field of TYPE_TEXT is stored as an array of characters without a null terminator. (Computable; Host form)

	TYPE_TEXT_LIST	  -  A text list. A field of TYPE_TEXT_LIST consists of a LIST structure which specifies the number of items in the list, followed by an array in which each element contains the length of each item in the list, followed by a packed character array with the text of the items. The text items are packed into the array without null terminators. (Computable; Host form)

	TYPE_NUMBER	  -  A number. A field of TYPE_NUMBER is stored using the C type double. (Computable; Host form)

	TYPE_NUMBER_RANGE	  -  A list of numbers. A field of TYPE_NUMBER_RANGE consists of a RANGE structure (which contains the number of items in the list) followed by a sequence of NUMBER structures. Number ranges are not currently supported by Domino. Therefore, the RangeEntries field of the RANGE structure should always be zero with fields of TYPE_NUMBER_RANGE. (Computable; Host form)

	TYPE_TIME	  -  A date/time field. A field of TYPE_TIME is stored in the Domino binary time/date format. (Computable; Host form)

	TYPE_TIME_RANGE	  -  A list of date/times and/or a list of date/time ranges. A field of TYPE_TIME_RANGE consist of a RANGE structure (which contains the number of items in the list, followed by the number of items specified as ranges), followed by a sequence of TIMEDATE structures, followed by a sequence of TIMEDATE_PAIR structures. (Computable; Host form)

	TYPE_FORMULA	  -  A $FORMULA item in a view note. A field of TYPE_FORMULA is the $FORMULA item in a view note. It consists of the compiled view selection formula and the compiled column formulas, with the appropriate summary items set. See the descriptions of the functions NSFFormulaCompile(), NSFFormulaSummaryItem(), and NSFFormulaMerge() for more details. (Computable; Host form)

	TYPE_USERID	  -  A Notes V1/V2 Author field: user name and license ID. A field of TYPE_USERID is a Notes V1/V2 Author field. It consists of a text user name and optional server names in parenthesis, followed by an 8 byte license ID. This type is obsolete in Notes 3.0 or later. See Data Type : Item (Field) Information : Author Names for the Notes 3.0 or later format for document author fields. (Computable; Host form)

	TYPE_INVALID_OR_UNKNOWN	  -  Returned by NSFItemInfo in the argument "value_datatype" when NSFItemInfo is not able to find an item. (Non-Computable; Host form)

	TYPE_COMPOSITE	  -  Rich text. A field of TYPE_COMPOSITE is a rich text field. A rich text field may contain many types of objects, including text, tables, document links, pictures, and DDE links. >64K handled by more than one item of same name concatenated. (See Rich Text datatypes). (Non-Computable; Canonical form)

	TYPE_COLLATION	  -  A $COLLATION item in a view note. A field of TYPE_COLLATION is the $COLLATION item in a view note, which describes how data is sorted in each column in the view. (Non-Computable; Canonical form)

	TYPE_OBJECT	  -  (Non-Computable; Canonical form)

	TYPE_NOTEREF_LIST	  -  A $REF (Response Reference List) item. A field of TYPE_NOTEREF_LIST is a Response Reference List. All response documents contain a Response Reference List item, which indicates that the document is a response note. A Response Reference List item has field name "$REF". The Response Reference consists of a LIST header structure, followed by the UNIVERSALNOTEID of the parent document. (Non-Computable; Host form)

	TYPE_VIEW_FORMAT	  -  A $VIEWFORMAT item in a view note. A field of TYPE_VIEW_FORMAT is the $VIEWFORMAT item in a view note, which defines the format of a view. It consists of a VIEW_TABLE_FORMAT structure, followed by a sequence of VIEW_COLUMN_FORMAT structures (one for each column in the view), followed by a VIEW_TABLE_FORMAT2 structure. See the descriptions of these structures for more details. (Non-Computable; Canonical form)

	TYPE_ICON	  -  (Non-Computable; Canonical form)

	TYPE_NOTELINK_LIST	  -  A $Links (Doc Link Reference List) item. A field of TYPE_NOTELINK_LIST is a Doc Link Reference List. Domino and Notes append a DocLink Reference List item to documents that contain Doc Links. A DocLink Reference Item has field name "$Links". A DocLink Reference List consists of a LIST header structure, followed by an array of NOTELINK structures. (Non-Computable; Host form)

	TYPE_SIGNATURE	  -  (Non-Computable; Canonical form)

	TYPE_SEAL	  -  (Non-Computable; Canonical form)

	TYPE_SEALDATA	  -  (Non-Computable; Canonical form)

	TYPE_SEAL_LIST	  -  (Non-Computable; Canonical form)

	TYPE_HIGHLIGHTS	  -  (Non-Computable; Host form)

	TYPE_WORKSHEET_DATA	  -  Used ONLY by Chronicle product. (Non-Computable; Canonical form)

	TYPE_USERDATA	  -  Arbitrary format data. (Non-Computable; Canonical form)

	TYPE_QUERY	  -  Saved query CD records. (Non-Computable; Canonical form)

	TYPE_ACTION	  -  Saved action CD records. (Non-Computable; Canonical form)

	TYPE_ASSISTANT_INFO	  -  Saved assistant info. (Non-Computable; Canonical form)

	TYPE_VIEWMAP_DATASET	  -  Saved ViewMap dataset (Non-Computable; Canonical form)

	TYPE_VIEWMAP_LAYOUT	  -  Saved ViewMap layout. (Non-Computable; Canonical form)

	TYPE_LSOBJECT	  -  Saved LotusScript Object code for an agent.

	TYPE_HTML	  -  LMBCS-encoded HTML, >64K handled by more than one item of same name concatenated.

	TYPE_SCHED_LIST	  -  Busy time schedule entries list. (Non-computable; Host form)

	TYPE_CALENDAR_FORMAT	  -  (Non-Computable; Canonical form)

	TYPE_MIME_PART	  -  MIME body part; Canonical form

	TYPE_RFC822_TEXT	  -  RFC822( RFC2047) message header; Canonical form


**Description :**

These values define the datatype of an item (field) in a note.<br>
<br>
All datatypes below are passed to NSF in either host (machine-specific byte ordering and padding) or canonical form (Intel 86 packed form).  The format of each datatype, as it is passed to and from NSF functions, is listed below in the comment field next to each of the data types.  (This host/canonical issue is NOT applicable to Intel86 machines, because on that machine, they are the same and no conversion is required).  On all other machines, use the ODS subroutine package to perform conversions of those datatypes in canonical format before they can be interpreted.<br>
<br>
Here is the format of the various LIST data types:<br>
<br>
TYPE_TEXT_LIST:<br>
    LIST /* list header */<br>
    USHORT ... /* array of text string lengths following */<br>
    text /* now comes the packed text for all strings */<br>
<br>
TYPE_NUMBER_RANGE:<br>
    RANGE /* range header */<br>
    NUMBER ... /* array of NUMBERs */<br>
    NUMBER_PAIR ... /* array of NUMBER_PAIRs */<br>
<br>
TYPE_TIME_RANGE:<br>
    RANGE /* range header */<br>
    TIMEDATE ... /* array of time/date's */<br>
    TIMEDATE_PAIR ... /* array of time/date pairs */<br>
<br>
TYPE_NOTEREF_LIST:<br>
    LIST /* list header */<br>
    UNIVERSALNOTEID /* array of UNIVERSALNOTEIDs */<br>
<br>
TYPE_NOTELINK_LIST:<br>
    LIST /* list header */<br>
    NOTELINK ... /* array of NOTELINKs */<br>
 <br>
TYPE_USERDATA:<br>
    BYTE Length /* length of LMBCS &quot;format-name&quot; string */<br>
    char[Length]; /* LMBCS &quot;format-name&quot; string used to distinguish various formats of user<br>
                                  data that follows. (&quot;format-name&quot; string is NOT NULL-TERMINATED!) */<br>
    data /* next is variable-length data that corresponds to the format specified by the string */


**See Also :**
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
---
