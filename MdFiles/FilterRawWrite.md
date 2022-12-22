




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




**Initial Release 6**



**Data Type : DSAPI**



**FilterRawWrite** **-** Write
content


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**




typedef
struct {


        char\*                  content;


        unsigned
int   contentLen;


        unsigned
int   reserved;


}
FilterRawWrite;


 


**Description :**



content -
Input/Output parameter. It is a pointer to a buffer that contains the data to
send to the client. The filter can change the data in place (using the same
buffer) or allocate a new buffer and fill it.


 


contentLen Input/Output
parameter. It is the number of valid bytes in the supplied buffer on input,
and/or the number of valid bytes in the buffer on output.


 


reserved**-** reserved for future use.


 




----------------------------------------------------------------------------------------------------------


 





