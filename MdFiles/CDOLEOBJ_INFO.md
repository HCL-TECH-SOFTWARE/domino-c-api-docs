




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




**Initial Release 4.5**



**Data Type : Composite Data; OLE**



**CDOLEOBJ\_INFO** **-** Specifies a
connection to an OLE object.


**----------------------------------------------------------------------------------------------------------**



**#include
<oleods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;          /\* Signature and length of this record \*/  

   WORD  FileObjNameLength; /\* Name of extendable $FILE object


                            
containing object data \*/  

   WORD  DescriptionNameLength; /\* Length of object description \*/  

   WORD  FieldNameLength; /\* Length of field name in which object


                            
resides \*/  

   WORD  TextIndexObjNameLength; /\* Name of the $FILE object


                            
containing LMBCS text for object \*/  

   OLE\_GUID OleObjClass;  /\* OLE ClassID GUID of OLE object \*/  

   WORD  StorageFormat;   /\* see OLE\_STG\_FMT\_xxx \*/       

   WORD  DisplayFormat;   /\* see DDEFORMAT\_xxx \*/  

   DWORD Flags;           /\* see OBJINFO\_FLAGS\_xxx \*/  

   WORD  StorageFormatAppearedIn; /\* Version # of Notes,


                            
high byte=major, low byte=minor,


                            
for display purposes \*/  

   WORD  HTMLDataLength;  /\* Length of HTML data for object \*/  

   WORD  AssociatedFILEsLength;  /\* Length of Associated $FILEs data for object
\*/  

   WORD  Reserved3;       /\* Unused, must be 0 \*/  

   DWORD Reserved4;       /\* Unused, must be 0 \*/  

/\* The variable length portions go here in the following order:


      FileObjectName  

      DescriptionName  

      Field Name in Document in which this object resides  

      Full Text index $FILE object name  

      HTML Data


          
Associated $FILEs Data


\*/  

} CDOLEOBJ\_INFO;


 


**Description :**



This
structure specifies a connection to an OLE object.


 **See Also :**


**[OLE\_STG\_FMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/858073E32C8EEA0D852563B7004D67CB)**


**[DDEFORMAT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255D28006FB649)**


**[OBJINFO\_FLAGS\_xxx](OBJINFO_FLAGS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





