




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



**Data Type : Composite Data; Rich
Text**



**CDRESOURCE** **-** A CD
structure which defines a Domino Resource.


**----------------------------------------------------------------------------------------------------------**



**#include
<rsrcods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD Flags;            /\* one of CDRESOURCE\_FLAGS\_xxx \*/  

   WORD  Type;             /\* one of CDRESOURCE\_TYPE\_xxx \*/  

   WORD  ResourceClass;    /\* one of CDRESOURCE\_CLASS\_xxx \*/  

   WORD  Length1;          /\* meaning depends on Type \*/  

   WORD  ServerHintLength; /\* length of the server hint \*/  

   WORD  FileHintLength;   /\* length of the file hint \*/  

   BYTE  Reserved[8];  

/\* Variable length follows:  

 \*   String of size ServerHintLength: hint as to resource's server  

 \*   String of size FileHintLength: hint as to resource's file  

 \*  - if CDRESOURCE\_TYPE\_URL :   

 \*     string of size Length1 - the URL.  

 \*  - if CDRESOURCE\_TYPE\_NOTELINK:   

 \*     if CDRESOURCE\_FLAGS\_NOTELINKINLINE is NOT set in Flags:  

 \*       WORD LinkID - index into $Links  

 \*       string of size Length1 - the anchor name (optional)  

 \*     if CDRESOURCE\_FLAGS\_NOTELINKINLINE is set in Flags:  

 \*       NOTELINK NoteLink  

 \*       string of size Length1 - the anchor name (optional)  

 \*  - if CDRESOURCE\_TYPE\_NAMEDELEMENT :  

 \*         TIMEDATE ReplicaID (zero if current db)


 \*         string of
size Length1 - the name of element  

 \*/  

} CDRESOURCE;


 


**Description :**



This CD
record defines a resource within a database.  There may be many resources
defined within a particular database.  A resource can be an image, an applet, a
shared field or a script library.


 


WSIG         Header                         Signature
and length


DWORD     Flags                            CDRESOURCE\_FLAGS\_xxx


WORD       Type                            CDRESOURCE\_TYPE\_xxx


WORD       ResourceClass             CDRESOURCE\_CLASS\_xxx


WORD       Length1                                    depends
on type           


WORD       ServerHintLength          length
of the server hint


WORD       FileHintLength              length
of the file hint      


BYTE         Reserved


 


 **See Also :**


**[CDRESOURCE\_CLASS\_xxx](CDRESOURCE_CLASS_xxx.md)**


**[CDRESOURCE\_FLAGS\_xxx](CDRESOURCE_FLAGS_xxx.md)**


**[CDRESOURCE\_TYPE\_xxx](CDRESOURCE_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





