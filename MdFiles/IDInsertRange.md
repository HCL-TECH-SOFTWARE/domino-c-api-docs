




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




}**Initial Release 9.0**



**Function : ID Table**



**IDInsertRange** **- Insert a
DWORD   Range of  IDs into ID Table**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS **IDInsertRange(**  

      DHANDLE  hTable,  

      DWORD  IDFrom,  

      DWORD  IDTo,  

      BOOL  AddToEnd**);**



**Description :**



This routine validates the given table. Also validates the
range to verify whether replacement required for existing IDs. It will not
insert unless both ranges are aligned. The Existing entries will be shifted
either before or after new range. if AddtoEnd flag is true it is assumed caller
is guaranteed that the ID range does not overlap any IDs in the table and are
the largest IDs in the table. This routine removes those entries  present in
the new  range  that is going to be inserted.   It is assumed that the ID space
is relatively "regular", that is, that ID values differ from each
other by some regular value, say 4. 


 


**Parameters :**



Input :  

hTable  -  handle of the table  

  

IDFrom  -  from range  

  

IDTo  -  to range  

  

AddToEnd  -  is add to end of table  

  




Output :  

(routine)  -  routine return status from this call. Either success or whatever
the error is.  

  

  




 **Sample Usage :**


STATUS 
ParseRecords(char \*buffer)


               {


               char tag[6];


               char \*ptag = tag;


               char \*p;


               DWORD
IDFrom, IDTo;


               char
buffercopy[400];


               BOOL
parsed = FALSE;


               


               //LogMessage("parsing
record %s", buffer);


               strncpy(buffercopy,
buffer, sizeof(buffercopy));


               p
= strtok(buffer," ");


 


               while (p != NULL)


                              {


                              //depending on
what the tag is, read the rest of the line


                              if( (strcmp(p, "ARBSKIP") == 0) ||
(strcmp(p, "ARS") == 0) || (strcmp(p, "BRSKIP") == 0) ||


                                              (strcmp(p,
"ARSKIP") == 0) ||
(strcmp(p, "BRBSKIP") == 0) )


                                             {


                                             parsed
= TRUE;


                                             //printf("ARBSKIP
record, next 2 entries are the range of id's\n");


                                             p
= strtok(NULL, " ");


                                             IDFrom
= strtol(p, &p, 16);


                                             p
= strtok(NULL, " ");


                                             IDTo
= strtol(p, &p, 16);


                                             //printf("Inserting
0x%x to 0x%x into table\n", IDFrom, IDTo);


 


                                             IDInsertRange
(hTable, IDFrom, IDTo, FALSE);


                                             return(NOERROR);


                                             }


 


                              else if( (strcmp(p, "SPACE") == 0) ||
(strcmp(p, "BIGSPACE") == 0) || (strcmp(p, "ASSIGN") == 0) ||


                                             (strcmp(p,
"ARUNALIGN") == 0) ||
(strcmp(p, "BRUNALIGN") == 0)            )


                                             {


                                             parsed
= TRUE;


                                             //printf("ignoring
line %s\n", buffercopy);


                                             return(NOERROR); 


                                             }


               


                              p
= strtok(NULL, " ");


                              }


 


               if(!parsed)


                                             printf("ignoring
line %s\n", buffercopy);


 


               return(NOERROR);


               }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





