




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
 {font-family:"MS Mincho";
 panose-1:2 2 6 9 4 2 5 8 3 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
 {font-family:"\@MS Mincho";
 panose-1:2 2 6 9 4 2 5 8 3 4;}
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




**Initial Release 7.0.2**



**Data Type : HTML**



**HTMLAPIReference** **-** the complete
reference of converted HTML result


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef struct {


 


      HTMLAPI\_REF\_TYPE  RefType;    /\*
How ref is used in the HTML text (HTMLAPI\_REF\_xxx - see list above) \*/


      char              \*pRefText;  /\*
Reference's NULL-terminated text string \*/


      CmdId             CommandId;  /\*
A web server command associated with the target URL \*/


      HTMLAPI\_URLComponent
\*pTargets;     /\* Reference's target components \*/


      HTMLAPI\_URLComponent    \*pArgs;     /\*
Reference's arguments (eg, &Start=xxx, &Count=xxx, etc). \*/


      DWORD             NumTargets; /\*
Number of components in the target part of the reference (dbname, unid, etc.)
\*/


      DWORD             NumArgs;    /\*
Number of components in the args part of the reference (&Start, etc.) \*/


      char              \*pFragment;
/\* NULL-terminated LMBCS text string -- the fragment part of URL


                                                            if
there is no fragment, pointer points to "" (i.e. '\0') \*/


 


      /\*
The rest of struct is variable in length.  Use the pointers


       \*
in the elements above here to access data from here on down.


       \*/


      HTMLAPI\_URLComponent
URLParts[1];   /\* C trick to align first member of an array of target and arg
values \*/


                                    /\*
Then come the reference's target strings, arg strings, and text string \*/


}
HTMLAPIReference;


 


**Description :**



HTMLAPIReference is
the complete reference of converted HTML result. To understand this data structure
more clearly, we will set an example here.


Suppose
there exist a section with a database named picture.nsf. The section's format
is like below:


 


 


Below is a
section :


      1.
section part 1


      2.
section part 2


After the HTML
tranlation,  the HTML code transformed from the section is like below :


 


<a name
="\_Section1"></a>


<a
href="/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&ExpandSection=-1#\_Section1"
target="\_self">


<img height="16"
width="16" src='/icons/collapse.gif' border="0"
alt="Hide details for Below is a section:">


</a>


Below is a section:


<ul>


1. section part 1<br>


2. section part 2<br>


</ul>


 


To
explain the HTMLAPIReference data structure more clearly, we will explain it
with below bitmap:


 


![](HTMLAPIReference_files/image001.png)


 


 


1 
           ;The reference Type is HTMLAPI\_REF\_HREF (RefType)


2             ;The URL
command is OpenDocument (CommandId)


3 
           ;Reference Text (pRefText)


4             ;The number of
HTMLAPI\_URLTargetComponent within this HTMLAPIReference is 2


5,6,7
      ;The first
HTMLAPI\_URLTargetComponent's detailed information


8,9          
;The second
HTMLAPI\_URLTargetComponent's detailed information


10           
;The URL
command's Argument is ExpandSection


11           
;The value of
the URL command's Argument is -1


 


 **See Also :**


**[HTMLAPI\_REF\_TYPE](HTMLAPI_REF_TYPE.md)**


**[HTMLAPI\_URLComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0ECD84DE44EACDEC482571960042001D)**



----------------------------------------------------------------------------------------------------------


 





