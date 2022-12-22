




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



**CDTEXT** **-** Begins a
text run in a rich-text field.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG   Header; /\* Tag and length \*/  

   FONTID FontID; /\* Font ID \*/


/\* The 8-bit text string
follows... \*/  

} CDTEXT;


 


**Description :**



This
structure defines the start of a run of text in a rich-text field.   

  

The FontID part of the structure controls the font, size, and color of the
text. See FONTIDFIELDS for the sub-structure of FontID.  

  

The overall structure for a rich-text field is:  

  

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

  

  

Rich text resides in items of type TYPE\_COMPOSITE.  For portablility to Unix
and other non-Intel architecture platforms, API programs must convert each CD
record in a rich text item to Domino canonical format before appending the data
to a note, and must convert each CD record to Host format after reading the
data from a note. See functions ODSReadMemory, ODSWriteMemory, and the sample
code below.


 **Sample Usage :**


/\* calculate how long
the canonical format buffer must be \*/     

  

wBuffLen =  ODSLength( \_CDPABDEFINITION ) +   

            ODSLength( \_CDPARAGRAPH )     +   

            ODSLength( \_CDPABREFERENCE )  +  

            ODSLength( \_CDTEXT )          +  

            wString1Len                   +  

            ODSLength( \_CDTEXT )          +  

            wString2Len                   ;  

      

  

rt\_field = (BYTE \*) malloc ( wBuffLen );  

  

/\* Keep a pointer to our current position in the buffer. \*/  

                

buff\_ptr = rt\_field;  

                

/\* ... steps missing... \*/  

  

/\* Add the CDTEXT record to the field. A CDTEXT record consists  

   of a CDTEXT structure followed by a run of text. Initialize the  

   CDTEXT structure by filling in the signature and the length.   

   The CDTEXT structure also contains the font information that  

   controls how Notes displays this first run of text.   

 \*/  

  

cdtext.Header.Signature = SIG\_CD\_TEXT;  

cdtext.Header.Length = ODSLength( \_CDTEXT ) + wString1Len ;  

  

pFontID = (FONTIDFIELDS \*) &(cdtext.FontID);  

    

pFontID->Face = FONT\_FACE\_SWISS;  

pFontID->Attrib = ISBOLD;  

pFontID->Color = NOTES\_COLOR\_BLUE;  

pFontID->PointSize = 24;  

  

ODSWriteMemory( &buff\_ptr, \_CDTEXT, &cdtext, 1 );  

  

/\* Write the actual characters of this first text tun to the buffer.   

   Since the run of text may contian embedded null characters, use   

   memcpy, not strcpy. No need to terminate the run of text with a   

   null because the Header.Length member of the CDTEXT structure   

   specifies the length explicitly.  

 \*/  

  

memcpy( (char \*)buff\_ptr, szString1, wString1Len );  

buff\_ptr += wString1Len;  

      

  

/\* ... steps missing ...\*/  

  

rt\_size = (DWORD)(buff\_ptr - rt\_field);  

  

error = NSFItemAppend( note\_handle,  

            0,  

            "RICH\_TEXT", strlen("RICH\_TEXT"),  

            TYPE\_COMPOSITE,  

            rt\_field, rt\_size );  

  

free( rt\_field );


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[CDPABREFERENCE](CDPABREFERENCE.md)**


**[CDPARAGRAPH](CDPARAGRAPH.md)**


**[NSFItemAppend](NSFItemAppend.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





