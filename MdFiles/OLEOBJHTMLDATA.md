




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0**



**Data Type : HTML; OLE Data Object**



**OLEOBJHTMLDATA** **-** OLE Object -
HTML Data.


**----------------------------------------------------------------------------------------------------------**



**#include
<oleods.h>**



**Definition :**



typedef struct {                                                         

   WORD  wLength;               /\* Size of this structure including


                                   both
fixed and variable


                                  
sections \*/  

   WORD  wsURLBaseLength;       /\* Length of Base URL \*/  

   WORD  wsURLCodeBaseLength;   /\* Length of CodeBase URL \*/  

   WORD  wsMIMETypeCodeLength;  /\* Length of MIME CodeType \*/  

   WORD  wsURLDataLength;       /\* Length of Data URL \*/  

   WORD  wsDataFldLength;       /\* Length of Data Field name \*/  

   WORD  wsDataSrcLength;       /\* Length of Data Source ID \*/  

   DWORD dwFlags;               /\* Flags \*/  

   WORD  wsLangLength;          /\* Length of Language \*/  

   WORD  wsNameLength;          /\* Length of Name \*/  

   WORD  wsMIMETypeDataLength;  /\* Length of MIME Type \*/  

   WORD  wcEvents;              /\* Number of events \*/  

   WORD  wcParams;              /\* Number of params \*/  

   WORD  wHeight;               /\* Height of object \*/  

   WORD  wWidth;                /\* Width of object \*/  

   WORD  wReserved1;            /\* Unused, must be 0 \*/  

   WORD  wReserved2;            /\* Unused, must be 0 \*/  

   WORD  wReserved3;            /\* Unused, must be 0 \*/  

   WORD  wReserved4;            /\* Unused, must be 0 \*/  

   WORD  wReserved5;            /\* Unused, must be 0 \*/  

   WORD  wReserved6;            /\* Unused, must be 0 \*/  

/\*


   The variable length
portions go here in the following order:


   URLBase - Base URL  

   CodeBase - URL that references where to find implementation of the object.   

   CodeType - MIME type of the code referenced by CLSID  

   Data - URL of the data to be loaded  

   Data Field - column name from the data source object  

   Data Source - "#ID" of the data source object  

   Lang - ISO standard language abbreviation  

   Name - variable name  

   Type - MIME type of Data attribute.  

   Events - array or list of events (OLEOBJHTMLEVENT structures)  

   Params - array or list of params (OLEOBJHTMLPARAM structures)  

\*/  

} OLEOBJHTMLDATA;


 


 **See Also :**


**[OLEOBJHTMLEVENT](OLEOBJHTMLEVENT.md)**


**[OLEOBJHTMLPARAM](OLEOBJHTMLPARAM.md)**



----------------------------------------------------------------------------------------------------------


 





