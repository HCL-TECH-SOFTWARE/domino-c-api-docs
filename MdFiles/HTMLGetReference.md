




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




**Initial Release 7.0.2**



**Function : HTML**



**HTMLGetReference** **- Get
reference from the HTML converter**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLGetReference(**  

      HTMLHANDLE  hHTML,  

      DWORD  Index,  

      MEMHANDLE  phRef**);**



**Description :**




 1) A
reference is a HTML reference in the notes generated HTML output. For example,
if there exist a section in the notes document. The section is as below:


 


 


 


  The HTML
output generated from this section will be like as below:


 


<a
name="\_Section1"></a><a href="/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&ExpandSection=-1#\_Section1"
target="\_self">


<img
height="16" width="16" src="/icons/collapse.gif"
border="0" alt="Hide details for Below is a
section:"></a>


This is a
section:


<ul>


1. section
part 1<br>


2. section
part2<br>


</ul>


 


The text in
pink color is an example of HTML reference converted from a notes document. in
this reference , it has two targets(please refer to the DATA structure
HTMLAPIReference).One target is the name of the nsf database where the notes
document locates in.The other target is the section's unid within the
picture.nsf database.


 


 2) This API
will get all the references from the HTML converter. From the reference, you
can get the other informations which are releated with the reference(please
refer to the     data structure HTMLAPIReference) and then parse them and deal
with them.


 


 3) Call
HTMLLockAndFixupReference on 'phRef' in order to access the reference data.


 


**Parameters :**



Input :  

hHTML  -  handle to the converter  

  

Index  -  zero relative index of the reference in the list of references  

  




Output :  

(routine)  -  NOERROR - Successful.  

 ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error status as a string that you may display/log for the user.  

  

  

phRef  -  memory handle of reference.  The handle is to a COPY of the reference
information.Caller is responsible for freeing the memory.   

  




 **Sample Usage :**


    DWORD retval = 0;


       
MEMHANDLE hRef = 0;


       
HTMLAPIReference \*pRef = 0;


        const
char\* newRefText = getenv("HAPI\_NewRefText");  


        char
\*temp = NULL;


       
STATUS rslt;


        rslt
= HTMLGetProperty(cvtr, HTMLAPI\_PROP\_NUMREFS, &retval);


        cerr
<< "<HAPI:RefList count=" << retval << endl;


        for
( int refi = 0 ; refi < retval; refi++ )


        {


       
rslt = HTMLGetReference(cvtr, refi, &hRef);


               


               if(rslt)


               {


                       PrintAPIError(rslt);


                       return
rslt;


               }


               rslt
= HTMLLockAndFixupReference(hRef, &pRef);


               if(rslt)


               {


                       PrintAPIError(rslt);


                       return
rslt;


               }


        }


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_REF\_TYPE](HTMLAPI_REF_TYPE.md)**


**[HTMLHANDLE](HTMLHANDLE.md)**


**[HTMLLockAndFixupReference](HTMLLockAndFixupReference.md)**


**[HTMLSetReferenceText](HTMLSetReferenceText.md)**



----------------------------------------------------------------------------------------------------------


 





