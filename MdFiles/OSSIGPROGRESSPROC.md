




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



**OSSIGPROGRESSPROC** **-** Function
pointer template for progress bar signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include
<ossignal.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR OSSIGPROGRESSPROC)(


   WORD Option,


   void \* Data1,


   void \* Data2);


 


**Description :**



Definition
of a pointer to a function that will handle the progress bar signal.  The
progress signal handler displays a progress bar.  The progress position will
generally start at 0 and end at Range.  The current progress supplied is either
absolute (SETPOS) or a delta from the previous progress state (DELTAPOS).  As
the operation which is supplying progress information is peformed, the range
may change.  If it does, an additional SETRANGE will be signaled.  

  

This signal handler requires three parameters:  

  

    Option - Values are defined in PROGRESS\_SIGNAL\_xxx.  

  

    Data1 - DWORD.  See the following table for detail.


                         
  

    Data2 - DWORD.  See the following table for detail.  

  






|  |  |  |
| --- | --- | --- |
| Option | Data1 | Data2 |
| **PROGRESS\_SIGNAL\_BEGIN** | NULL | NULL |
| **PROGRESS\_SIGNAL\_END** | NULL | NULL |
| **PROGRESS\_SIGNAL\_SETRANGE** | Range | NULL |
| **PROGRESS\_SIGNAL\_SETTEXT** | pointer
 to the text (pText1) | NULL |
| **PROGRESS\_SIGNAL\_SETPOS** | New
 progress bar position | NULL |
| **PROGRESS\_SIGNAL\_DELTAPOS** | Delta
 of the progress bar position | NULL |
| **PROGRESS\_SIGNAL\_SETBYTERANGE** | Total
 bytes | NULL |
| **PROGRESS\_SIGNAL\_SETBYTEPOS** | Bytes
 done | NULL |


 


 **Sample Usage :**



OSSIGPROGRESSPROC
ProgressProc;


char
STARTTEXT[100]="Look at the progress";


int  i;


   .


   .


   .


 


/\* Get the
Progress signal handler function pointer. \*/


**ProgressProc =
(OSSIGPROGRESSPROC) OSGetSignalHandler(OS\_SIGNAL\_PROGRESS);**



/\* Start the
Progress signal. \*/


**(\*ProgressProc)(PROGRESS\_SIGNAL\_BEGIN,NULL,NULL);**



/\* Set the
header of the Progress bar. \*/


**(\*ProgressProc)(PROGRESS\_SIGNAL\_SETTEXT,(DWORD)STARTTEXT,NULL);**



/\* Set the
starting position. \*/


**(\*ProgressProc)(PROGRESS\_SIGNAL\_SETPOS,
0,NULL);**



/\* Set the
range. \*/


**(\*ProgressProc)(PROGRESS\_SIGNAL\_SETRANGE,1000,NULL);**




/\* Let's see the
Progress. \*/


for
(i=2;i<1000;i++)


{


  (**\*ProgressProc)(PROGRESS\_SIGNAL\_SETPOS,
i,NULL);**


}


 


/\* It's done. \*/


(**\*ProgressProc)(PROGRESS\_SIGNAL\_END,NULL,NULL);**



 **See Also :**


**[OSSIGPROC](OSSIGPROC.md)**


**[PROGRESS\_SIGNAL\_xxx](PROGRESS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





