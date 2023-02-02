##### Data Type : Composite Data
##### CDFIELDHINT - Record defining a text "hint" associated with a field
---
##### #include <editods.h>
**Description :**
The designer of a form may define a "hint" associated with a field. This 
descriptive text is visible in dimmed text within the field when a document is 
created using the form and helps the user to know what to select or fill in for 
the field. This text does not get saved with the document and disappears when 
the cursor enters the field.  

If the Flags member is set to FIELDHINT_LIMITED, a CDFIELDHINT record contains 
hint information for a limited number of object types in a Rich Text Lite 
field. Rich Text Lite fields are rich text fields in which limits are imposed 
on the types of objects stored in it.  In addition to object types such as 
"pictures" or "shared images", "clear" (to clear the contents of the field) and 
"help" may be stored.  If the "help" option is selected, the dimmed text within 
the field will dynamically change to provide a "hint" for the object type 
selected. For a field with hint information for limited object types, the 
CDFIELDHINT record may be followed by a CDDATAFLAGS structure. 

The CDFIELDHINT record is preceded by a CDFIELD record. The CDFIELDHINT record 
is followed by variable length data whose length is specified in the 
HintTextLength member. This variable length data specifies the field hint. A 
CDFIELDHINT record may be present for both the field hint and the field limits 
hint. 

The fields in this record are:

Header - Signature and Length of this CD record
HintTextLength - Length of the field hint
Flags - see FIELDHINT_xxx
Spare
Spare2

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[CDDATAFLAGS](D:/md_files/CDDATAFLAGS.md)
[CDFIELD](D:/md_files/CDFIELD.md)
[FIELDHINT_xxx](D:/md_files/FIELDHINT_xxx.md)
---
