




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



**ODSLength** **- Get the
length of a data structure in Domino canonical format**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



WORD
LNPUBLIC **ODSLength(**  

      WORD  type**);**



**Description :**



This
function returns the length, in bytes, of a data structure in Domino canonical
format.  Use this function when calculating the buffer size needed to contain
data structures converted to Domino canonical format.  

  

Domino canonical format is defined as Intel-architecture byte ordering with no
pad bytes.  All data in Domino database files is stored in canonical format. On
Intel-architecture machines, the ODS length of a data structure is the same as
the sizeof() that data structure.    

  

Normally, on Intel-architecture machines, data types need not be aligned to
addresses which are multiples of the data type size.  On non-Intel systems,
however, a data type is normally aligned on an address which is a multiple of
the data type size.  This means that on non-Intel systems, many data structures
contain unused bytes.  Therefore, the overall length of a data structure in
memory (machine specific format) may be greater than when stored in a Domino
database file on disk (canonical format).  The ODSLength function provides a
way for API programs to determine the size of a data structure when converted
to Domino canonical format.


 


**Parameters :**



Input :  

type  -  ODS type word - identifies the Domino data structure.  The ODS type
symbol is the underscore character followed by the Domino data structure name.
For example,  \_CDPARAGRAPH identifies a CDPARAGRAPH data structure. See
Symbolic Value \_xxx (ODS Types) for a list of the valid ODS type words.  

  




Output :  

(routine)  -  Length of the data structure in Domino canonical format  

  

  




 **Sample Usage :**



    /\*  

 \* Create the $VIEWFORMAT item (also known as "View Table Format
item"). The $VIEWFORMAT   

 \* item is an item of TYPE\_VIEW\_FORMAT with name VIEW\_VIEW\_FORMAT\_ITEM.  

 \*  

 \* The $VIEWFORMAT item for this view will consist of the following   

 \* series of structures converted to Domino canonical format and packed
together:  

 \*  

 \*          VIEW\_TABLE\_FORMAT  

 \*          VIEW\_COLUMN\_FORMAT (for column 1)  

 \*          VIEW\_COLUMN\_FORMAT (for column 2)  

 \*          VIEW\_COLUMN\_FORMAT (for column 3)  

 \*          Item Name for column 1  

 \*          formula for column 1  

 \*          Item Name for column 2  

 \*          Title for column 2  

 \*          formula for column 2  

 \*          Item Name for column 3  

 \*          Title for column 3  

 \*          formula for column 3  

 \*          VIEW\_TABLE\_FORMAT2


     \*  

 \*  

 \* First, allocate a buffer, pViewFormatBuffer, that will contain the   

 \* entire $VIEWFORMAT item.   

 \*/  

        

  

    wViewFormatBufLen = ODSLength( \_VIEW\_TABLE\_FORMAT )   +  

                        ODSLength( \_VIEW\_COLUMN\_FORMAT )  +  

                        ODSLength( \_VIEW\_COLUMN\_FORMAT )  +  

                        ODSLength( \_VIEW\_COLUMN\_FORMAT )  +  

                        wItemName\_1\_Len                   +  

                        wFormula\_1\_Len                    +  

                        wItemName\_2\_Len                   +  

                        wTitle\_2\_Len                      +  

                        wFormula\_2\_Len                    +  

                        wItemName\_3\_Len                   +  

                        wTitle\_3\_Len                      +  

                        wFormula\_3\_Len                    +  

                        ODSLength( \_VIEW\_TABLE\_FORMAT2 )  ;  

    

  

    if (sError = OSMemAlloc( 0, wViewFormatBufLen, &hViewFormatBuffer ))  

    {  

         printf("Error: unable to allocate %d bytes memory.\n",   

            wViewFormatBufLen);  

         goto Exit3;  

    }


 **See Also :**


**[ODSReadMemory](ODSReadMemory.md)**


**[ODSWriteMemory](ODSWriteMemory.md)**


**[\_xxx (ODS Types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6624318DA38E8A885255F18007069DE)**



----------------------------------------------------------------------------------------------------------


 





