




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




 


**Data Type : IDs**



**DBID** **-** Identifies a
database.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



**|** #if \_MSC\_VER >= 1600


/\* MS VS
2010 typedefs it's own DBID so we get a conflict here like so:


 


   797:
c:\sb\v90dnp\inc\nsfdata.h(106) : error C2371: 'DBID' : redefinition; different
basic types


   798:
c:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\include\oledb.h(718) : see
declaration of 'DBID'


 


   Instead
of renaming our DBID or modifying the system header we simply use the


  
preprocessor to avoid the issue altogether.  The only way we would get


   a
conflict again is if someone intends to use the MS DBID and includes both


   this
header and oledb.h \*/


#define
DBID TIMEDATE


#else


typedef
TIMEDATE DBID;


#endif


 


**Description :**



This is the
structure that uniquely identifies a particular database instance.  This DBID
will be different for each replica of the same database.


 **See Also :**


**[TIMEDATE](TIMEDATE.md)**


**[NSFDbIDGet](NSFDbIDGet.md)**



----------------------------------------------------------------------------------------------------------


 





