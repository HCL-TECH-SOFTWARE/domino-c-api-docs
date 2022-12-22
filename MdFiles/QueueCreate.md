




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



**QueueCreate** **- Create a
new FIFO queue**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
FAR PASCAL **QueueCreate(**  

      DHANDLE \*rtnhandle**);**



**Description :**



This
function will create a new FIFO queue. It  will eventually have to have two
semaphores associated with it.  The first will be an "event" that is
signalled once for each queue entry that is present.  At the top of the GET
procedure, a wait-for-event operation will cause the caller to suspend until a
queue entry is present.  The PUT procedure will signal this event whenever
entering an entry on the queue.  The second semaphore will be a
"lock" that prevents multiple processes calling GET from
simultaneously clobbering the QUEUE\_HEADER structure.  It will simply lock the
header operations.


 


**Parameters :**




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

rtnhandle  -  A pointer to a handle of the newely created queue  

  




 **Sample Usage :**


/\*  Start the directory
search \*/


    


        if
(error = QueueCreate(&hQueue))


               goto
done\_search;


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





