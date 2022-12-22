




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




**Initial Release 4.0**



**Data Type : Replication**



**REPLEXTENSIONS** **-** Replication
extension structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<repl.h>**



**Definition :**



typedef struct {  

   WORD     Size;      /\* sizeof(REPLEXTENSIONS), allows for future  

                          expansion \*/  

   WORD     TimeLimit; /\* If non-zero, number of minutes replication  

                          is allowed to execute before cancellation.  

                          If not specified, no limit is imposed \*/  

} REPLEXTENSIONS;


 


**Description :**



To allow
upwardly compatible changes with arbitrary additional parameters in
ReplicateWithServer.  Only TimeLimit is defined for Release 4.  The parameter
corresponding to this structure in ReplicateWithServerExt(), ExtendedOptions,
may be set to NULL as a shorthand for passing a completely zeroed structure.


 **See Also :**


**[ReplicateWithServerExt](ReplicateWithServerExt.md)**



----------------------------------------------------------------------------------------------------------


 





