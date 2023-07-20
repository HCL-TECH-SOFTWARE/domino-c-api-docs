##### Data Type : Composite Data
##### CDTEXT - Begins a text run in a rich-text field.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG   Header; /* Tag and length */
   FONTID FontID; /* Font ID */
/* The 8-bit text string follows... */
} CDTEXT;
```

**Description :**

This structure defines the start of a run of text in a rich-text field. <br>
<br>
The FontID part of the structure controls the font, size, and color of the text. See FONTIDFIELDS for the sub-structure of FontID.<br>
<br>
The overall structure for a rich-text field is:<br>
<br>
CDPABDEFINITION    <br>
CDPABDEFINITION    <br>
CDPABDEFINITION    <br>
...<br>
CDPARAGRAPH	  <br>
CDPABREFERENCE<br>
CDTEXT<br>
text	<br>
CDTEXT	<br>
text<br>
CDTEXT	<br>
text<br>
...<br>
CDPARAGRAPH	  <br>
CDPABREFERENCE<br>
CDTEXT<br>
text	<br>
CDTEXT	<br>
text<br>
...<br>
<br>
<br>
Rich text resides in items of type TYPE_COMPOSITE.  For portablility to Unix and other non-Intel architecture platforms, API programs must convert each CD record in a rich text item to Domino canonical format before appending the data to a note, and must convert each CD record to Host format after reading the data from a note. See functions ODSReadMemory, ODSWriteMemory, and the sample code below.


**Sample Usage :**
```
/* calculate how long the canonical format buffer must be */   

wBuffLen =  ODSLength( _CDPABDEFINITION ) + 
            ODSLength( _CDPARAGRAPH )     + 
            ODSLength( _CDPABREFERENCE )  +
            ODSLength( _CDTEXT )          +
            wString1Len                   +
            ODSLength( _CDTEXT )          +
            wString2Len                   ;
    

rt_field = (BYTE *) malloc ( wBuffLen );

/* Keep a pointer to our current position in the buffer. */
              
buff_ptr = rt_field;
              
/* ... steps missing... */

/* Add the CDTEXT record to the field. A CDTEXT record consists
   of a CDTEXT structure followed by a run of text. Initialize the
   CDTEXT structure by filling in the signature and the length. 
   The CDTEXT structure also contains the font information that
   controls how Notes displays this first run of text. 
 */

cdtext.Header.Signature = SIG_CD_TEXT;
cdtext.Header.Length = ODSLength( _CDTEXT ) + wString1Len ;

pFontID = (FONTIDFIELDS *) &(cdtext.FontID);
  
pFontID->Face = FONT_FACE_SWISS;
pFontID->Attrib = ISBOLD;
pFontID->Color = NOTES_COLOR_BLUE;
pFontID->PointSize = 24;

ODSWriteMemory( &buff_ptr, _CDTEXT, &cdtext, 1 );

/* Write the actual characters of this first text tun to the buffer. 
   Since the run of text may contian embedded null characters, use 
   memcpy, not strcpy. No need to terminate the run of text with a 
   null because the Header.Length member of the CDTEXT structure 
   specifies the length explicitly.
 */

memcpy( (char *)buff_ptr, szString1, wString1Len );
buff_ptr += wString1Len;
    

/* ... steps missing ...*/

rt_size = (DWORD)(buff_ptr - rt_field);

error = NSFItemAppend( note_handle,
            0,
            "RICH_TEXT", strlen("RICH_TEXT"),
            TYPE_COMPOSITE,
            rt_field, rt_size );

free( rt_field );
```

**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
[CDPARAGRAPH](/domino-c-api-docs/reference/Data/CDPARAGRAPH)
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[ODSWriteMemory](/domino-c-api-docs/reference/Func/ODSWriteMemory)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
