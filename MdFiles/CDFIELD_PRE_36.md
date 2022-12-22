




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



**CDFIELD\_PRE\_36** **-** \* OBSOLETE \*
Defines the attributes of a field in a form.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



  

/\*   

 \* (\*\*\* OBSOLETE \*\*\*) Pre-V1 Field Reference Record,   

 \*  used in Forms (\*\*\* OBSOLETE \*\*\*)   

 \*/  

  

typedef struct {  

    WSIG Header;  

    WORD Flags;            /\* Field Flags \*/  

    WORD DataType;         /\* Alleged NSF Data Type \*/  

    WORD ListDelim;               /\* List Delimiters \*/  

    NFMT NumberFormat;     /\* Number format, if applicable \*/      

    TFMT TimeFormat;       /\* Time format, if applicable \*/  

    FONTID FontID;         /\* displayed font \*/  

    WORD DVLength;         /\* Default Value Formula \*/  

    WORD ITLength;         /\* Input Translation Formula \*/  

    WORD Unused1;          /\* Unused \*/  

    WORD IVLength;         /\* Input Validity Check Formula \*/  

    WORD NameLength;       /\* NSF Item Name \*/  

    WORD DescLength;       /\* Description of the item \*/  

                          /\* Now comes variable part of the struct... \*/  

  

} CDFIELD\_PRE\_36;         /\* List of Text Values was added... \*/  

  




 


**Description :**



This item is
an obsolete definition of the attributes of a field in a form note. It is
included in this reference for compatibility with forms created with pre-V1
releases of Notes.  

  

Header:                  Defines this composite data item as a CDFIELD item.  

Flags:                      Defines some field attributes (see Fxxx).  

DataType              Defines the datatype of the field being defined (see
FIELD\_TYPE\_xxx).  

ListDelim                Defines the delimiters used to separate multi-values
in a field. See LDELIM\_xxx, LDDELIM\_xxx.  

NumberFormat    If this is a number field, defines the number format.  See
NFMT.  

TimeFormat          If this is a timedate field, defines the time format. See
TFMT.  

FontID                      Defines the font to be used in this field.  See
FONTID.  

DVLength               Length of this field's compiled Default Value formula.  

ITLength                 Length of this field's compiled Input Translation
formula.      

Unused1                 This field is unused, and should be set to zero.  

IVLength                 Length of this field's compiled Default Value formula.  

NameLength         Length of the name of this field.  

DescLength           Length of the description of this field.  

  

The above items are then followed by a series of zero or more packed strings,
corresponding to the "length" parameters listed above. These packed
strings must appear in the same order as the "length" parameters  

  




 **See Also :**


**[CDFIELD](CDFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





