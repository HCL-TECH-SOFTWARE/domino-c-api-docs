




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
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
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




}


**Function : ID Table**



**IDTableReplaceExtended** **- Replace
an ID table with the contents of another ID table**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS **IDTableReplaceExtended(**  

      DHANDLE  hSrcTable,  

      DHANDLE  hDstTable,  

      WORD  Flags**);**



**Description :**



Replace an ID table with the contents of another ID table.
This routine validates both source and destination before start the routine . also
checks both tables are H format if one of the table is H format. and clears the
inverted tables which are used in the routine if IDTABLE\_INVERTED flag set


 


**Parameters :**



Input :  

hSrcTable  -  ID table to copy  

  

hDstTable  -  ID table to be replaced  

  

Flags  -  IDREPLACE\_SAVEDEST - The destination table's Time and Flags are
preserved with the exception of   

the IDTABLE\_INVERTED flag which is propagated from the source table. This is
used by IDTableReplace  

  

  




Output :  

(routine)  -  routine return status from this call. Either success or whatever
the error is.  

  

  




 **Sample Usage :**


STATUS
IDTableReplaceExtended(DHANDLE hSrcTable, DHANDLE hDstTable, WORD Flags)


               {


                              m\_qstate->setcoreFuncName(\_\_FUNCTION\_\_);


#ifdef DQL\_RELIABILITY\_TEST


                              if (Developer())


                              {


                                             m\_qstate->incrCoreCallCount(1,
&m\_bThrowError);


                                             if
(m\_bThrowError)


                                                            return
commonIDTRets();


                              }


#endif


                              return
::IDTableReplaceExtended(hSrcTable, hDstTable, Flags);


               }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





