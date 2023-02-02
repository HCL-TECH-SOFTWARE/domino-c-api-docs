##### Data Type : Composite Data
##### CDHEADER - Header/Footer record
---
##### #include <editods.h>
**Description :**
Contains the header or footer used in a document.

        Header                                Tag identifying this as a header 
or footer record
        FontPitchAndFamily        Pitch and font family of font used to display 
the data
        FontName                           Name of font to use
        Font                                       ID of font to use
        HeadLength                       Total string length of header or footer

This header structure is followed by the string for the header or footer.
**See Also :**
[CDDOCUMENT](D:/md_files/CDDOCUMENT.md)
---
