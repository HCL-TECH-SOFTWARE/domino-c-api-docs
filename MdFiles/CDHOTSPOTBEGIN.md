




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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




 


**Data Type : Composite Data; Rich
Text**



**CDHOTSPOTBEGIN** **-** Specifies
the start of a hotspot.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header; /\* Signature and length of this record \*/        

   WORD  Type;  

   DWORD Flags;  

   WORD  DataLength;  

/\*  Data follows... \*/


    /\*  if
HOTSPOTREC\_RUNFLAG\_SIGNED, WORD SigLen then SigData follows. \*/


}
CDHOTSPOTBEGIN;


 


**Description :**



This
structure specifies the start of a "hot" region in a rich text
field.  Clicking on a hot region causes some other action to occur.  For
instance, clicking on a popup will cause a block of text associated with that
popup to be displayed.


 


Normally,
each CDHOTSPOTBEGIN record is followed by records describing the hotspot and
any associated action formula and, finally, a CDHOTSPOTEND record.  There are
special cases for Release 4.x, Release 5.x and 6 hotspot records which have
either Lotus Script or Release 4.x (or 5.x or 6) actions associated with them. 
These hotspots contain a CDHOTSPOTBEGIN record with the signature
SIG\_CD\_V4HOTSPOTBEGIN (or SIG\_CD\_V5HOTSPOTBEGIN or
SIG\_CD\_V6HOTSPOTBEGIN\_CONTINUATION), and a CDHOTSPOTEND record with the
signature SIG\_CD\_V4HOTSPOTEND (or SIG\_CD\_V5HOTSPOTEND).


 


The fields
in this record are:


  

 
Header:     Defines this composite data item as a


             
CDHOTSPOTBEGIN item.  

  Type:       Specifies the type of hotspot.


              See
HOTSPOTREC\_TYPE\_xxx.  

  Flags:      Defines some of the hotspot's attributes.


              See
HOTSPOTREC\_RUNFLAG\_xxx  

  DataLength: Specifies the length of the variable-length


              data for
this item.  

  

The above fields are then followed by some variable length data, the format of
which is dependent on the type of hotspot that is being defined.  The variable
length data for the different hotspot types is as follows:


 


*       
If the Type is HOTSPOTREC\_TYPE\_POPUP and the 
HOTSPOTREC\_RUNFLAG\_FORMULA flag is not set, then the variable-length data is a
packed string containing the popup's static text.


*       
If the Type is HOTSPOTREC\_TYPE\_POPUP and the 
HOTSPOTREC\_RUNFLAG\_FORMULA flag is set, then the variable-length data is the
compiled formula that will generate the popup's text.


*       
If theType is HOTSPOTREC\_TYPE\_BUTTON then the variable-length data
is the button's compiled formula.


*       
If the Type is HOTSPOTREC\_TYPE\_FILE then the variable-length data
consists of two null-terminated strings. The first string is the internal
unique file name assigned to the attached file by Domino or Notes. The second
string is the original name of the file.


*       
If the Type is HOTSPOTREC\_TYPE\_HOTLINK and the HOTSPOTREC\_RUNFLAG\_INOTES
flag is set, then the variable-length data is a packed string containing the
URL's static text.


*       
If the flag HOTSPOTREC\_RUNFLAG\_SIGNED is set, the variable-length
data determined by the hotspot type and other flags is followed by a WORD containing
the length of the digital signature, then the digital signature for the
hotspot.


  

Note that rich text fields are items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.


 **See Also :**


**[CDHOTSPOTEND](CDHOTSPOTEND.md)**


**[HOTSPOTREC\_TYPE\_xxx](HOTSPOTREC_TYPE_xxx.md)**


**[HOTSPOTREC\_RUNFLAG\_xxx](HOTSPOTREC_RUNFLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





