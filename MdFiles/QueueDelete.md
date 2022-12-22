




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




 


**Function : Miscellaneous**



**QueueDelete** **- Delete a
queue object.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
FAR PASCAL **QueueDelete(**  

      DHANDLE  queue**);**



**Description :**



Delete a
queue object, usually after all its contents have been fetched using a loop
calling QueueGet.  QueueDelete can be called before a queue has been fully
processed, but it will return ERR\_QUEUE\_NOT\_EMPTY if so.


 


**Parameters :**



Input :  

queue  -  The handle to the queue which is to be deleted  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_QUEUE\_NOT\_EMPTY - The queue is not empty.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


if (err =
NSFSearchStart(search\_db, fhandle, NULL, NULL,


                                                     qhandle,
flags, noteclass,


                                                     NOTE\_CLASS\_NONE,
granularity,


                                                     since,
&until, &shandle))


               {


               QueueDelete(qhandle);


               goto
done;


               }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





