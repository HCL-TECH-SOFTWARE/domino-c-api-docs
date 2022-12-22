




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



**CDOLEBEGIN** **-** Specifies
the start of an OLE Object


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header;           /\* Signature and length of this record \*/  

   WORD Version;          /\* Notes OLE implementation version \*/  

   DWORD Flags;           /\* See OLEREC\_FLAG\_xxx \*/  

   WORD ClipFormat;             /\* Clipboard format with which data should   

                              be rendered (see DDEFORMAT\_xxx) \*/  

   WORD AttachNameLength;  /\* Attached file name length \*/  

   WORD ClassNameLength;   /\* Length of readable OLE class name \*/  

   WORD TemplateNameLength; /\* User during Insert New Object,   

                               but never saved to disk \*/  

/\* The Attachment Name (len=AttachNameLength) always follows... \*/  

/\* The Classname (optional) then follows... \*/  

/\* The Template Name (optional) then follows... \*/  

} CDOLEBEGIN;


 


**Description :**



This
structure specifies the start of an OLE Object.  

  

Note that rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.  

  

  Header:                           Defines this composite data item as a
CDOLEBEGIN item.  

  Version:                           Notes OLE implementation version. Set this
to NOTES\_OLEVERSION.  

  Flags:                              Defines various attributes of the OLE
object. See OLEREC\_FLAG\_xxx.  

  ClipFormat:                      Clipboard format with which to render data. 
See DDEFORMAT\_xxx.  

  AttachNameLength:         Filename length (without the '\0' terminator) of
the attached OLE object file.  

  ClassNameLength:          (Optional) Length of the object's readable OLE
class name.  

  TemplateNameLength:     (Optional) Length of the object's template class
name.  

  

The above fields are then followed by a series of zero or more packed strings,
corresponding to the "length" parameters listed above.  These packed
strings must appear in the same order as the "length" parameters.


 **See Also :**


**[CDOLEEND](CDOLEEND.md)**



----------------------------------------------------------------------------------------------------------


 





