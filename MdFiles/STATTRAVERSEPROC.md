




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




 


**Data Type : Statistics Reporting**



**STATTRAVERSEPROC** **-** Action
routine for each statistic found by StatTraverse().


**----------------------------------------------------------------------------------------------------------**



**#include
<stats.h>**



**Definition :**



typedef STATUS
(LNPCALLBACKPTR STATTRAVERSEPROC)(  

   void far \*, /\* Context   - ptr to data passed to StatTraverse to


                             
be given to this routine \*/  

   char far \*, /\* Facility  - facility name \*/  

   char far \*, /\* StatName  - name of statistic \*/  

   WORD,       /\* ValueType - see VT\_xxx \*/  

   void far \*  /\* Value     - value of the statistic \*/  

);


 


**Description :**



This typedef
defines the interface to the routine called by StatTraverse().  Under Windows,
the routine must be exported in the application's .DEF file.


 


The address
of a routine with this interface is passed as a parameter to StatTraverse(). 
The routine will be called once for each statistic found.  The first parameter
is supplied in the call to StatTraverse() and is used in the case where the
caller of StatTraverse() needs to pass data to this routine.  If this routine
returns an error, the traversal will halt and return that error.


 **See Also :**


**[StatTraverse](StatTraverse.md)**



----------------------------------------------------------------------------------------------------------


 





