




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



**Data Type : LDAP**



**timeval** **-** LDAP time
value structure


**----------------------------------------------------------------------------------------------------------**



**#include
<ldap.h>**



**Definition :**



/\*


  \*   Time structure


  \*/


 


#if defined(UNIX)


#include
<sys/time.h>


/\*  timeval is defined
in <winsock2.h>, inc\wsock16.h, and inc\wsock32.h for Windows builds.\*/


#elif !defined(W)


typedef struct timeval 


    {


    long    tv\_sec;        /\*
seconds \*/


    long    tv\_usec;       /\*
and microseconds \*/


    } timeval;


 


#endif


 


**Description :**



Implementations
of the LDAP API MUST ensure that the struct timeval type is by default defined
as a consequence of including the ldap.h header.  Because struct timeval is
usually defined in one or more system headers, it is possible for header
conflicts to occur if ldap.h also defines it or arranges for it to be defined
by including another header.  Therefore, applications MAY want to arrange for
struct timeval to be defined before they include ldap.h.  To support this, the
ldap.h header MUST NOT itself define struct timeval if the preprocessor symbol
LDAP\_TYPE\_TIMEVAL\_DEFINED is defined before ldap.h is included.


 




----------------------------------------------------------------------------------------------------------


 





