




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



**Data Type : Composite Data; Rich
Text**



**CDFIELDHINT** **-** Record
defining a text "hint" associated with a field


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


    WSIG    Header;        /\*
Tag and length \*/


    WORD    HintTextLength;


    WORD    Flags;         /\*
See above \*/


    WORD    Spare;


    DWORD   Spare2;


                                  /\*
The 8-bit text string follows... \*/


} CDFIELDHINT;


 


**Description :**



The designer
of a form may define a "hint" associated with a field. This
descriptive text is visible in dimmed text within the field when a document is
created using the form and helps the user to know what to select or fill in for
the field. This text does not get saved with the document and disappears when
the cursor enters the field.  


 


If the Flags
member is set to FIELDHINT\_LIMITED, a CDFIELDHINT record contains hint
information for a limited number of object types in a Rich Text Lite field.
Rich Text Lite fields are rich text fields in which limits are imposed on the
types of objects stored in it.  In addition to object types such as "pictures"
or "shared images", "clear" (to clear the contents of the
field) and "help" may be stored.  If the "help" option is
selected, the dimmed text within the field will dynamically change to provide a
"hint" for the object type selected. For a field with hint
information for limited object types, the CDFIELDHINT record may be followed by
a CDDATAFLAGS structure. 


 


The
CDFIELDHINT record is preceded by a CDFIELD record. The CDFIELDHINT record is
followed by variable length data whose length is specified in the
HintTextLength member. This variable length data specifies the field hint. A
CDFIELDHINT record may be present for both the field hint and the field limits
hint. 


 


The fields
in this record are:


 


Header -
Signature and Length of this CD record


HintTextLength
- Length of the field hint


Flags - see
FIELDHINT\_xxx


Spare


Spare2


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 **See Also :**


**[CDDATAFLAGS](CDDATAFLAGS.md)**


**[CDFIELD](CDFIELD.md)**


**[FIELDHINT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6AEC602AAA5F17F785256A2A006561DB)**



----------------------------------------------------------------------------------------------------------


 





