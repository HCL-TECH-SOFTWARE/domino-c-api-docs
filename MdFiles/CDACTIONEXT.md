




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




**Initial Release 6**



**Data Type : Composite Data; Form;
Rich Text**



**CDACTIONEXT** **-** Extended
field attributes for CDACTION


**----------------------------------------------------------------------------------------------------------**



**#include
<actods.h>**



**Definition :**



typedef
struct 


               {


               WSIG     Header;                                                              /\*
Signature and Length \*/


               DWORD dwFlags;                                                             /\*
Reserved for future use. \*/


               WORD   wControlType;                                    /\*
Type of control. See ACTION\_CONTROL\_TYPEs below. \*/


               WORD   wControlFormulaLen;                         /\*
Length of formula following this CD record. Formula use depends on the control
type \*/


               WORD   wLabelFormulaLen;                            /\*
Length of formula following this CD record. Formula is used for
control's/menu's label. \*/


               WORD   wParentLabelFormulaLen;  /\*
Length of formula following this CD record. Formula is used for
control's/menu's "parent" label when action is first in a group. \*/


               WORD   wCompActionIDLen;                          /\*
Length of name of action ID (from composite definition). \*/


               WORD   wProgrammaticUseTxtLen;               /\*
Length of the Program Use attribute \*/


               DWORD dwExtra[2];                                                         /\*
available for future use. \*/


               }
CDACTIONEXT;


 


**Description :**



New field attributes
have been added in Notes/Domino 6.  To preserve compatibility with existing
applications, the new attributes have been placed in this extension to the
CDACTION record.  This record is optional, and may not be present in the $Body
item of the form note.


 


In R5, a
view action's hide whens, and hence state, is only evaluated once when the view
is loaded. Notes/Domino 6 allows the action's state to be evaluated each time a
different document becomes current. A checkbox in the action bar and/or a
checked item on the action menu can change to reflect a value in the currently
selected document. The control formula value evaluates to true (checked) or
false (unchecked). The wControlType member of CDACTIONEXT must be
ACTION\_CONTROL\_TYPE\_CHECKBOX and the view must allow for evaluating actions for
every document changed . 


 


The fields
in this structure are:


 


Header -
Defines this composite data item as a CDACTIONEXT item.


 


dwFlags -
Reserved for future use.


 


wControlType
- See ACTION\_CONTROL\_TYPE\_xxx.


 


wControlFormulaLen
- Length of formula following this CD record.


 


wLabelFormulaLen
- Length of formula following this CD record. Formula is used for
control's/menu's label.


 


wParentLabelFormulaLen
- Length of formula following this CD record. 


 


  
 wCompActionIDLen
- Length of name of action ID (from composite definition). 


 


  
 wProgrammaticUseTxtLen
- Length of the Program Use attribute


 


dwExtra -
Reserved for future use.


 


These fields
may be followed by an optional control formula value. If you plan to use it,
you will need to declare the variable and assign a value to its length.


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 


 **See Also :**


**[ACTION\_CONTROL\_TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/29E2B749944B7837852569D6005844DD)**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





