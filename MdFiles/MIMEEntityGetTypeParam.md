




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



**Function : MIME**



**MIMEEntityGetTypeParam** **- Get the
string value and length of a MIME parameter for the input MIME entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEEntityGetTypeParam(**  

      PMIMEENTITY  pMIMEEntity,  

      MIMESYMBOL  symParam,  

      DHANDLE \*phValue,  

      DWORD \*pdwValueLen**);**



**Description :**



This
function MIMEEntityGetTypeParam returns a handle to the value of the input
parameter, symParam, in the location pointed to by phValue.  It also returns
the length of the parameter value in the location pointed to by pdwValueLen.  The
string is everything after the '='.  If the current entity does not contain the
parameter indicated by symParam, MIMEEntityGetTypeParam returns the error
ERR\_MIME\_NO\_DATA.  If pMIMEEntity is NULL or if symParam is MIME\_SYMBOL\_UNKNOWN
or MIME\_SYMBOL\_NONE, MIMEEntityGetTypeParam returns ERR\_MISC\_INVALID\_ARGS.


  The caller
is responsible for freeing the phValue memory.


 


 


**Parameters :**



Input :  

pMIMEEntity  -  a pointer to current MIME entity.  

  

symParam  -  the MIMESYMBOL for the desired parameter.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the
parameter value memory.  

     ERR\_MISC\_INVALID\_ARGS - returned for various input parameter errors.  

     ERR\_MIME\_NO\_DATA - returned if the requested parameter is not found.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

phValue  -  a handle to an allocated block of memory containing the parameter
value.  

  

pdwValueLen  -  the length of the parameter value string in bytes.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


DHANDLE hParam;


DWORD dwParamLen;


const char
\*pszHeaderValue;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


if (error =
MIMEEntityGetTypeParam(pRootEntity, MIME\_SYMBOL\_FILENAME, &hParam,
&dwParamLen)) {


        goto exit;


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 


 **See Also :**


**[MIMESYMBOL](MIMESYMBOL.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





