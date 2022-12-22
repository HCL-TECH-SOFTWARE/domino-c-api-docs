




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



**CDDDEBEGIN** **-** Specifies
the start of a DDE link.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct  

    {  

        WSIG Header;                  /\* Signature and length of   

                                         this record \*/  

        char ServerName[DDESERVERNAMEMAX];  /\* Null terminated   

                                               server name \*/  

        char TopicName[100];        /\* Null terminated DDE Topic  

                                       (usually a file name) \*/  

        char ItemName[DDEITEMNAMEMAX];  /\* Null terminated Place   

                                           reference string \*/  

        DWORD Flags;                /\* See DDEFLAGS\_xxx flag  

                                       definitions \*/  

                                       

        char PasteEmbedDocName[80]; /\* only used on when making   

                                       new link during Paste   

                                       Special \*/  

        WORD EmbeddedDocCount;      /\* Number of embedded docs   

                                       for this link \*/  

                                    /\* (MUST BE 0 or 1) \*/  

        WORD ClipFormat;            /\* Clipboard format with  

                                       which data should be   

                                       rendered \*/  

                                    /\* ( See DDEFORMAT\_xxx) \*/  

  

        /\* Null terminated embedded document name which is   

           attached to the note follows.. \*/  

        }CDDDEBEGIN;  

  




 


**Description :**



A CD record
of this type specifies the start of a DDE link.  

  

Note that CDDDEBEGIN records reside in items of type TYPE\_COMPOSITE. Therefore,
API programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these
records in an item in a note.


 **See Also :**


**[CDDDEEND](CDDDEEND.md)**



----------------------------------------------------------------------------------------------------------


 





