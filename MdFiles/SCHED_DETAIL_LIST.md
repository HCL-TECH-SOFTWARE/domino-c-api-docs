




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



**Data Type : Calendaring and
Scheduling**



**SCHED\_DETAIL\_LIST** **-** Schedule
detail list header.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {


    WORD       
wHeaderLen;     /\* Length of THIS header, in case it


                        
       \*\* ever grows, so that new items can be 


                               
\*\* easily skipped


                               
\*/


    WORD       
wEntryLen;      /\* Length of THIS entire list and ALL of 


                               
\*\* its related data.


                               
\*/


    WORD       
wNumEntries;    /\* Number of entries that follow \*/


    WORD       
wOffsetItems;   /\* Offset from list start to TEXT\_LIST \*/


    WORD       
wOffsetDetails; /\* Offset from list start to SCHED\_DETAIL\_ENTRY \*/


         BYTE       
Attr;           /\* SCHED\_DETAIL\_LIST\_ATTR\_xxx attributes \*/


    BYTE       
bReserved;      /\* Reserved space/padding for ODS \*/


 


    /\* Now comes the
TEXT\_LIST that corresponds to the item names 


    \*\* and then comes
the SCHED\_DETAIL\_ENTRY for each UNID


    \*/


} SCHED\_DETAIL\_LIST;


 


**Description :**



Schedule
detail list header.


 **Sample Usage :**


The following code
snippet illustrates a way to retrieve information from SCHED\_DETAIL\_LIST:


 


 


       
SCHED\_DETAIL\_LIST \* pList = (SCHED\_DETAIL\_LIST \*) pData;


           



       
/\* Points pItemList to the beginning of TEXT\_LIST (which follows the
SCHED\_DETAIL\_LIST structure) \*/


       
LIST \*  pItemList = (LIST \*) ( (char \*) pList + pList->wOffsetItems );  


               



       
WORD    wItemCount = ListGetNumEntries( pItemList, FALSE );


       
printf("List of item names matching the SCHED\_DETAIL\_DATA entries:
%d\n",wItemCount);


 


       
/\* points pSchedDetailEntry to the beginning of SCHED\_DETAIL\_ENTRY (which
follows the TEXT\_LIST) \*/


       
SCHED\_DETAIL\_ENTRY \*    pSchedDetailEntry = (SCHED\_DETAIL\_ENTRY \*) ( (char \*)
pList + pList->wOffsetDetails ); 


       
SCHED\_DETAIL\_DATA  \*    pSchedDetailData


 


       
/\* Loops through all the SCHED\_DETAIL\_ENTRY,lists the actual
SCHED\_DETAIL\_ENTRYs and their 


          
associated SCHED\_DETAIL\_DATA \*/


 


         for
(DWORD iEntry = 0; iEntry < pList->wNumEntries; iEntry++)


         {


              
printf("SCHED\_DETAIL\_ENTRY %d\n",iEntry);


              
if ( sizeof(SCHED\_DETAIL\_ENTRY) != pSchedDetailEntry->wOffsetDetails ){


                 
printf("Warning: entry header size is %d bytes but we expect only
%d\n",


                    
pSchedDetailEntry->wOffsetDetails,sizeof(SCHED\_DETAIL\_ENTRY));


              
}


              
/\* .


                 
.


                 
- - - you can print SCHED\_DETAIL\_ENTRY header information here - - -


              
\*/


 


              
if ( pSchedDetailEntry->wEntryLen == pSchedDetailEntry->wPrefixLen ) {


                 
printf("\*\*\* This SCHED\_DETAIL\_ENTRY contains NO SCHED\_DETAIL\_DATA
\*\*\*\n");


              
}


              
else


              
{


                 
/\* points pSchedDetailData to the beginning of SCHED\_DETAIL\_DATA \*/


                 
pSchedDetailData =  


                    
(SCHED\_DETAIL\_DATA \*) ( (char \*)pSchedDetailEntry+
pSchedDetailEntry->wOffsetDetails );                                


            
     /\* loops through all the SCHED\_DETAIL\_DATA for this SCHED\_DETAIL\_ENTRY \*/


                 
for (DWORD iData = 0; iData < wItemCount; iData++ )


                 
{


                    
printf("   \* SCHED\_DETAIL\_DATA %d\n",iData); 


                   
 /\* .


                       
.


                       
- - -  you can print SCHED\_DETAIL\_DATA header information here - - -


                    
\*/


 


                    
if ( pSchedDetailData->wDataLen ) {


                             
/\* .


             
                   .


                                
now you can print SCHED\_DETAIL\_DATA : 


                                   
the starting point would be pSchedDetailData + sizeof(SCHED\_DETAIL\_DATA)


                                   
the length would be pSchedDetailData->wDataLen


                              
\*/


                    
}


                    
/\* points to the next SCHED\_DETAIL\_DATA \*/


       
              pSchedDetailData = (SCHED\_DETAIL\_DATA \*) ( (char \*)
pSchedDetailData + 


                                       
pSchedDetailData->wDataLen + 


                                       
sizeof(BYTE) +


                                       
sizeof(WORD) +


                                       
sizeof(WORD) );


                  
}


              
}


 


              
/\* moves pointer to point to the next SCHED\_DETAIL\_ENTRY \*/


              
pSchedDetailEntry = (SCHED\_DETAIL\_ENTRY \*) ( (char \*) pSchedDetailEntry +
pSchedDetailEntry->wEntryLen);


 


         } 
/\* for (DWORD iEntry = 0; iEntry < pList->wNumEntries; iEntry++) \*/


 


 **See Also :**


**[LIST](LIST.md)**


**[SCHED\_DETAIL\_DATA](SCHED_DETAIL_DATA.md)**


**[SCHED\_DETAIL\_ENTRY](SCHED_DETAIL_ENTRY.md)**


**[SCHED\_DETAIL\_LIST\_ATTR\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ED48E29744D824A385256A2C004AABF8)**



----------------------------------------------------------------------------------------------------------


 





