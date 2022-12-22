




<!--
 /\* Font Definitions \*/
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




 


**Function : AddIn**



**OSPreemptOccasionally** **- Cause a
server add-in task to give up control.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**



void
LNPUBLIC **OSPreemptOccasionally(**void**);**



**Description :**



This
function causes a server add-in task to give up control, so that other tasks on
the machine can run.  It is intended to be used within compute-bound loops in a
server add-in task.  

  

This function only has an effect on operating systems, such as Windows, that do
not preempt compute-bound tasks.  Under preemptive operating systems, this
function does nothing.  

  

Under operating systems that need it, OSPreemptOccasionally is included within
the AddInIdle call.  Therefore, standard add-in task loops (that are not
compute bound) do not require OSPreemptOccasionally.  OSPreemptOccasionally is
quite fast however, so there is little penalty for including it in your
program.


 


**Parameters :**




Output :  

(routine)  -  None  

  

  




 **See Also :**


**[AddInIdle](AddInIdle.md)**



----------------------------------------------------------------------------------------------------------


 





