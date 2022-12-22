




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



**Data Type : Composite Data; Rich
Text**



**CDALTERNATEBEGIN** **-** Start of
alternate display records.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;         /\* Signature and length of this record \*/  

   WORD  Type;           /\* Type of active object this is an 


                              
alternate for \*/  

   DWORD SequenceNumber; /\* ID/Sequence number should match what's


                           
in some ACTIVEOBJECT in the doc \*/  

   DWORD Flags;          /\* Unused; must be 0 \*/  

   WORD  DataLength;     /\* Unused; must be 0 \*/  

/\* Data Follows. \*/  

} CDALTERNATEBEGIN;


 


**Description :**



Documents
converted from HTML (Hyper-Text Markup Language), usually from a World Wide Web
source, may contain "active object" instructions (such as a Java
applet).  An active object may have an alternate representation which is to be
displayed if the active object is not supported or is disabled.  When an active
object is converted to a compound text representation, the alternate
representation is stored beginning with a CDALTERNATEBEGIN record and ending
with a CDALTERNATEEND record.  An alternate representation corresponds to the
most recent active object with the same ACTIVEOBJECT\_TYPE\_xxx code, found in
the Type field.  The fields in this record are:


 


Header                         Identifies
this record as a CDALTERNATEBEGIN record


Type                            Type
of active object for which this representation is an alternate (see ACTIVEOBJECT\_TYPE\_xxx)


SequenceNumber         Sequence
number for the active object for which this representation is an alternate


Flags                            Currently
unused;  must be 0


DataLength                   Currently
unused;  must be 0


 


 **See Also :**


**[CDALTERNATEEND](CDALTERNATEEND.md)**


**[ACTIVEOBJECT\_TYPE\_xxx](ACTIVEOBJECT_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





