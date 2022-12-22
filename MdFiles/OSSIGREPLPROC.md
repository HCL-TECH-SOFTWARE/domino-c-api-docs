




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




**Initial Release 5.0.2**



**Data Type : Signal Handler**



**OSSIGREPLPROC** **-** Function
pointer template for replication state signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include
<ossignal.h>**



**Definition :**



typedef void
(LNCALLBACKPTR OSSIGREPLPROC)(


   WORD State,


   char far \*pText1,


   char far \*pText2);


 


**Description :**



Definition
of a pointer to a function that will handle the replication state signal.  


  

This replication state handler requires three parameters:  

  

   **State** - Values are defined in REPL\_SIGNAL\_xxx.  

  

    **pText1** - See the following table for detail.


 


            **pText2**- See the following table for detail.


   

  






|  |  |  |
| --- | --- | --- |
| State | pText1 | pText2 |
| **REPL\_SIGNAL\_IDLE** | None |   |
| **REPL\_SIGNAL\_PICKSERVER** | None |   |
| **REPL\_SIGNAL\_CONNECTING** | pServer | pPort |
| **REPL\_SIGNAL\_SEARCHING** | pServer | pPort |
| **REPL\_SIGNAL\_SENDING** | pServerFile | pLocalFile |
| **REPL\_SIGNAL\_RECEIVING** | pServerFile | pLocalFile |
| **REPL\_SIGNAL\_SEARCHINGDOCS** | pSrcFile |   |
| **REPL\_SIGNAL\_DONEFILE** | pLocalFile | pReplFileStats |


 


 


 **See Also :**


**[OSSIGPROC](OSSIGPROC.md)**


**[REPL\_SIGNAL\_xxx](REPL_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





