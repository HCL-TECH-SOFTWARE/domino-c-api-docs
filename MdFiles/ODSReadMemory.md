




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




 


**Function : Canonical Format
Conversion**



**ODSReadMemory** **- Convert a
structure from canonical format to machine-specific format.**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



void
LNPUBLIC **ODSReadMemory(**  

      void far \*ppSrc,  

      WORD  type,  

      void far \*pDest,  

      WORD  iterations**);**



**Description :**



This
function converts Domino data structures from Domino canonical format to
machine-specific (host) format. This writes the result into a variable or
memory buffer provided by the caller.  

  

You must convert data structures to host format before accessing the members of
the structure if (1) your API program runs on non-Intel architecture machines,
and (2) your API program is reading a Domino data item of one of the data types
listed below:  

  

    TYPE\_COMPOSITE  

    TYPE\_COLLATION  

    TYPE\_OBJECT  

    TYPE\_VIEW\_FORMAT  

    TYPE\_ICON  

    TYPE\_SIGNATURE  

    TYPE\_SEAL  

    TYPE\_SEALDATA  

    TYPE\_SEAL\_LIST  

    TYPE\_WORKSHEET\_DATA  

    TYPE\_USERDATA


   
TYPE\_QUERY


   
TYPE\_ACTION


   
TYPE\_ASSISTANT\_INFO


   
TYPE\_VIEWMAP\_DATASET


   
TYPE\_VIEWMAP\_LAYOUT


   
TYPE\_CALENDAR\_FORMAT  

  

For example, if your API program runs under UNIX and reads a CDFONTTABLE
structure from an item of type TYPE\_COMPOSITE, you must use ODSReadMemory() to
convert the CDFONTTABLE to machine-specific format before you access the members
of the CDFONTTABLE structure.  

  

If your API program runs under Windows, then ODSReadMemory() is not necessary,
but will do no harm. Therefore, code that uses ODSReadMemory() properly is
portable across platforms.  

  

For items of any data type other than those listed above, and for Domino data
structures in general, you must not use ODSReadMemory() because Domino and
Notes automatically convert such data to host format for you. Therefore, your
API program should directly access non-item data (e.g. note header data) and
data of other data types (such as TYPE\_TIME).  

  

Note that the data type word at the beginning of an item data value is almost
always in host format. When using functions such as NSFItemInfo() to read an
item value, the item value begins with a data type WORD. Domino and Notes
convert this data type WORD to host format for you, even if the rest of the
item data is in canonical format.  


 


There is an
exception with Domino database hook drivers and extension manager API
programs.  A Domino database hook driver or an extension manager API program
may receive all note item data, including the data type WORD in canonical
format.  A Domino hook driver or an extension manager that accesses note item
data over a network in which the note was not opened by the hook driver or
extension manager itself, must check the OpenFlags parameter in the NoteOpen
callback function (if the program is a database hook driver) or in the callback
function for EM\_NSFNOTEOPEN or EM\_NSFNOTEOPENBYUNID (if the program is an extension
manager) to see whether this flag is set. If this flag is set, use
ODSReadMemory to convert any note item data to host format.


 


 


**Parameters :**



Input :  

ppSrc  -  Address of a void pointer that points to the source memory buffer. 
ODSReadMemory reads the Domino canonical form data structure(s) from this
buffer.  

  

type  -  ODS type word - identifies the Domino data structure.  The ODS type
symbol is the underscore character followed by the Domino data structure name.
For example,  \_CDPARAGRAPH identifies a CDPARAGRAPH data structure.  See
Symbolic Value \_xxx (ODS Types) for a list of the valid ODS type words.  

  

iterations  -  Specifies the number of structures at the address specified by
pDest.  

  




Output :  

ppSrc  -  ODSReadMemory changes the specified void pointer to point to the next
byte after the canonical form of the Domino structure read from the buffer. 
This facilitates reading a sequence of structures in canonical form from a
buffer by making a sequence of calls to ODSReadMemory.  

  

pDest  -  Pointer to the variable or buffer to receive data in machine-specific
format.  Normally, this is the address of a variable of a type identified by
the type argument.  If iterations > 1, pDest specifies an array of
structures of that type.  The caller is responsible for ensuring that the
specified buffer has sufficient space to hold the data.  

  




 **Sample Usage :**


  

    void           \*pItemValue;  

    CDFONTTABLE     cdFontTab;  

    CDFACE          cdFace;  

    WORD            wIndex;  

  

   /\* RecordPtr points to the first byte of the item value after the  

      datatype word. The item value is in Domino canonical format. It  

      starts with a CDFONTTABLE structure. Call ODSReadMemory() to  

      convert this CDFONTTABLE to host format and store it in  

      cdFontTab. ODSReadMemory() increments pItemValue to point to  

      the next byte in the input buffer after the CDFONTTABLE.  

    \*/  

  

    pItemValue = RecordPtr;  

    ODSReadMemory( &pItemValue, \_CDFONTTABLE, &cdFontTab, 1 );  

  

    for (wIndex = 0; wIndex < cdFontTab.Fonts; wIndex++)  

    {  

        ODSReadMemory( &pItemValue, \_CDFACE, &cdFace, 1 );  

        printf( "    Font %d:\n", wIndex );  

        printf( "       Face    = %d\n", cdFace.Face );  

        printf( "       Family  = %d\n", cdFace.Family );  

        printf( "       Name    = %s\n", cdFace.Name );  

    }


 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[ODSLength](ODSLength.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[\_xxx (ODS Types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6624318DA38E8A885255F18007069DE)**



----------------------------------------------------------------------------------------------------------


 





