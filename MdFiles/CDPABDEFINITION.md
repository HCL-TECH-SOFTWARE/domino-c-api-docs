




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




 


**Data Type : Composite Data; Rich
Text**



**CDPABDEFINITION** **-** Defines a
format for rich-text paragraphs.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header;        /\* Used to quickly recognize structure type \*/  

   WORD PABID;         /\* ID of this PAB \*/  

   WORD JustifyMode;   /\* paragraph justification type \*/  

   WORD LineSpacing;   /\* (2\*(Line Spacing-1)) (0:1,1:1.5,2:2,etc) \*/  

   WORD ParagraphSpacingBefore; /\* # LineSpacing units above para \*/  

   WORD ParagraphSpacingAfter;  /\* # LineSpacing units below para \*/  

   WORD LeftMargin;    /\* leftmost margin, twips rel to abs left \*/  

                       /\* (16 bits = about 44") \*/  

   WORD RightMargin;   /\* rightmost margin, twips rel to abs right \*/  

                       /\* (16 bits = about 44") \*/  

                       /\* Special value "0" means right margin \*/  

                       /\* will be placed 1" from right edge of \*/  

                       /\* paper, regardless of paper size. \*/  

   WORD FirstLineLeftMargin; /\* leftmost margin on first line \*/  

                       /\* (16 bits = about 44") \*/  

   WORD Tabs;          /\* number of tab stops in table \*/  

   SWORD Tab[MAXTABS]; /\* table of tab stop positions, negative \*/  

                       /\* value means decimal tab \*/  

                       /\* (15 bits = about 22") \*/  

   WORD Flags;         /\* paragraph attribute flags - PABFLAG\_xxx \*/  

   DWORD TabTypes;     /\* 2 bits per tab \*/  

   WORD Flags2;        /\* extra paragraph attribute flags - PABFLAG2\_xxx \*/


} CDPABDEFINITION;


 


**Description :**



This
structure specifies a format for paragraphs in a rich-text field. There may be
more than one paragraph using the same paragraph format, but there may be no
more than one CDPABDEFINITION with the same ID in a rich-text field.    

  

Note: All units in the fields of this structure are in TWIPS (1/20 of a
point).  There are 72 points to an inch and 20 TWIPS to a point, and therefore
there are 72 \* 20 TWIPS to an inch.  Use the  #define ONEINCH to represent the
number of TWIPS to an inch.  For example:  

  

.LeftMargin = ONEINCH/2, .RightMargin = ONEINCH,  .FirstLineLeftMargin =
(ONEINCH + ONEINCH/2), .TAB[0] = ONEINCH, .TAB[1] = 2\*ONEINCH, etc.


 


As of R5, a
CDPABDEFINITION structure can be followed by an array of six WORDs of margin
values:


Margin [0]         -
Left margin offset in twips


Margin [1]         -
Left margin offset in percent (0 - 100)


Margin [2]         -
First line left margin offset in twips


Margin [3]         -
First line left margin offset in percent (0 - 100)


Margin [4]         -
Right margin offset in twips


Margin [5]         -
Right margin offset in percent (0 - 100)


 


If these
"extension" words are present after a CDPABDEFINITION structure in an
R5 database, then you should get the margin information from them.  If they are
not present, then your code should get its margin values from the LeftMargin,
FirstLineLeftMargin, and RightMargin elements of the CDPABDEFINITION
structures, as was done in R4.


 


If R5 margin
extension WORDs are present, then you can also use PABFLAG2\_xxx masks defined
in editdflt.h to tell which of the values to use:


 


PABFLAG2\_LM\_OFFSET


PABFLAG2\_LM\_PERCENT


PABFLAG2\_FLLM\_OFFSET


PABFLAG2\_FLLM\_PERCENT


PABFLAG2\_RM\_OFFSET


PABFLAG2\_RM\_PERCENT


  

If the Flags2 member of CDPABDEFINITION is set to PABFLAG2\_MORE\_FLAGS, the
CDPABDEFINITION may be followed by a DWORD extension. If the value of this
DWORD extension is EXTENDEDPABFLAGS3 (introduced in Notes/Domino 6), then a
second DWORD extension may be present with a value of PABFLAG3\_HIDE\_EE. These
DWORD extensions follow the six R5 margin extension WORDs, if they are present.


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.  

  

A rich text field consists of a series of CD records.  A paragraph in a rich
text field normally starts with a CDPARAGRAPH record, followed by a
CDPABREFERENCE record, followed by zero or more CDTEXT records.  The
CDPABREFERENCE record specifies which of the CDPABDEFINITION records that
appeared previously in the field define the paragraph style to use when
displaying this paragraph.   

  

The sequence of CD records in a typical rich-text field might be:  

  

CDPABDEFINITION      

CDPABDEFINITION      

CDPABDEFINITION      

...  

CDPARAGRAPH        

CDPABREFERENCE  

CDTEXT  

text   

CDTEXT      

text  

CDTEXT      

text  

...  

CDPARAGRAPH        

CDPABREFERENCE  

CDTEXT  

text   

CDTEXT      

text  

...


 **Sample Usage :**


/\* Initialize a
CDPABDEFINITION structure.  We use all defaults,   

   except for centered justification.   

 \*/  

  

pabdef.Header.Signature = SIG\_CD\_PABDEFINITION;  

pabdef.Header.Length = ODSLength( \_CDPABDEFINITION );  

pabdef.PABID = PARA\_STYLE\_ID;  

pabdef.JustifyMode = JUSTIFY\_CENTER;  

pabdef.LineSpacing = DEFAULT\_LINE\_SPACING;  

pabdef.ParagraphSpacingBefore = DEFAULT\_ABOVE\_PAR\_SPACING;  

pabdef.ParagraphSpacingAfter = DEFAULT\_BELOW\_PAR\_SPACING;  

pabdef.LeftMargin = DEFAULT\_LEFT\_MARGIN;  

pabdef.RightMargin = DEFAULT\_RIGHT\_MARGIN;  

pabdef.FirstLineLeftMargin = DEFAULT\_FIRST\_LEFT\_MARGIN;  

pabdef.Tabs = DEFAULT\_TABS;  

pabdef.Tab[0] = DEFAULT\_TAB\_INTERVAL;  

pabdef.Flags = 0;


    pabdef.TabTypes =
TAB\_DEFAULT;  

pabdef.Flags2 = DEFAULT\_FLAGS2;


  

/\* Call ODSWriteMemory to convert the CDPABDEFINITION structure to   

   Domino canonical format and write the converted structure into  

   the buffer at location buff\_ptr. This advances buff\_ptr to the  

   next byte in the buffer after the canonical format strucure.  

 \*/  

      

ODSWriteMemory( &buff\_ptr, \_CDPABDEFINITION, &pabdef, 1 );


 **See Also :**


**[CDPABREFERENCE](CDPABREFERENCE.md)**


**[CDPARAGRAPH](CDPARAGRAPH.md)**


**[CDTEXT](CDTEXT.md)**


**[EXTENDEDPABFLAGS3](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E48F9EDCE17226DF852569D7005F8FAF)**


**[PABFLAG2\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6EB5AA7C5103BB78852564BA004C3BC2)**


**[PABFLAG3\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA5ED726CA007728852569D7005FDC2B)**


**[PABFLAG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00E90052006E00DB85255E850077FA1A)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





