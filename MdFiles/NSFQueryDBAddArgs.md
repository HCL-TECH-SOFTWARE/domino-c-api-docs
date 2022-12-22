




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




 


**Function : Database**



**NSFQueryDBAddArgs** **- Build a
list of values to input into a Domino Query Language (DQL) query.**


**----------------------------------------------------------------------------------------------------------**



**#include <dbmisc.h>**



STATUS
 **NSFQueryDBAddArgs(**  

      QUEP\_ARGVAL \*pArg,  

      MEMHANDLE \*phQargList**);**



**Description :**



Build a
lists of values to input into a DQL query, specifying arguments through
QUEP\_ARGVAL structure. Validates QUEP\_ARGVAL structure and compares to stored
values. Returns NOERROR and MEMHANDLE (phQargList) if successful. If errors are
found in parsing arguments or if validation fails, returns
ERR\_MISC\_INVALID\_ARGS. If memory errors are found, returns ERR\_MEMORY.


 


**Parameters :**



Input :  

pArg  -  A value, ordinal, or name for the argument to build.   

  




Output :  

(routine)  -  Returns status from the call, either success or an error.   

   The return codes include:   

    NOERROR - On success.   

    ERR\_MISC\_INVALID\_ARGS - Invalid arguments.   

    ERR\_MEMORY - Memory failure.  

  

  

phQargList  -  Set of QUEP\_ARGVALs that were built.  

  




 **Sample Usage :**


      /\* To
build argument list for DQL 


            pArg
is pointer to a QUEP\_ARGVAL struct built prior to this call. \*/


            QUEP\_ARGVAL
pArg = {0};


            MEMHANDLE
phQArgList = NULLMEMHANDLE;


            pArg.type
= TYPE\_TEXT;


            strncpy(pArg.Value,
"\'This is another line of simple text.\'", sizeof(pArg.Value));


            pArg.length
= strlen(pArg.Value);


            pArg.bBinaryForm
= FALSE;


            if
(err = NSFQueryDBAddArgs(&pArg, &phQArgList))


                        goto
errout; 


            ...



            if
(err = NSFQueryDBExt2(..., phQArgList)) 


                        goto
errout;


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





