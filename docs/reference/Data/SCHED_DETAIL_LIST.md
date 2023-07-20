##### Data Type : Calendaring and Scheduling
##### SCHED_DETAIL_LIST - Schedule detail list header.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
    WORD        wHeaderLen;     /* Length of THIS header, in case it
                                ** ever grows, so that new items can be 
                                ** easily skipped
                                */
    WORD        wEntryLen;      /* Length of THIS entire list and ALL of 
                                ** its related data.
                                */
    WORD        wNumEntries;    /* Number of entries that follow */
    WORD        wOffsetItems;   /* Offset from list start to TEXT_LIST */
    WORD        wOffsetDetails; /* Offset from list start to SCHED_DETAIL_ENTRY 
*/
	 BYTE        Attr;           /* SCHED_DETAIL_LIST_ATTR_xxx attributes */
    BYTE        bReserved;      /* Reserved space/padding for ODS */

    /* Now comes the TEXT_LIST that corresponds to the item names 
    ** and then comes the SCHED_DETAIL_ENTRY for each UNID
    */
} SCHED_DETAIL_LIST;
```

**Description :**

Schedule detail list header.


**Sample Usage :**
```
The following code snippet illustrates a way to retrieve information from 
SCHED_DETAIL_LIST:


        SCHED_DETAIL_LIST * pList = (SCHED_DETAIL_LIST *) pData;
	    
        /* Points pItemList to the beginning of TEXT_LIST (which follows the 
SCHED_DETAIL_LIST structure) */
        LIST *  pItemList = (LIST *) ( (char *) pList + pList->wOffsetItems );  
                
        WORD    wItemCount = ListGetNumEntries( pItemList, FALSE );
        printf("List of item names matching the SCHED_DETAIL_DATA entries: 
%d\n",wItemCount);

        /* points pSchedDetailEntry to the beginning of SCHED_DETAIL_ENTRY 
(which follows the TEXT_LIST) */
        SCHED_DETAIL_ENTRY *    pSchedDetailEntry = (SCHED_DETAIL_ENTRY *) ( 
(char *) pList + pList->wOffsetDetails ); 
        SCHED_DETAIL_DATA  *    pSchedDetailData

        /* Loops through all the SCHED_DETAIL_ENTRY,lists the actual 
SCHED_DETAIL_ENTRYs and their 
           associated SCHED_DETAIL_DATA */

	 for (DWORD iEntry = 0; iEntry < pList->wNumEntries; iEntry++)
	 {
               printf("SCHED_DETAIL_ENTRY %d\n",iEntry);
               if ( sizeof(SCHED_DETAIL_ENTRY) != 
pSchedDetailEntry->wOffsetDetails ){
                  printf("Warning: entry header size is %d bytes but we expect 
only %d\n",
                     
pSchedDetailEntry->wOffsetDetails,sizeof(SCHED_DETAIL_ENTRY));
               }
               /* .
                  .
                  - - - you can print SCHED_DETAIL_ENTRY header information 
here - - -
               */

               if ( pSchedDetailEntry->wEntryLen == 
pSchedDetailEntry->wPrefixLen ) {
                  printf("*** This SCHED_DETAIL_ENTRY contains NO 
SCHED_DETAIL_DATA ***\n");
               }
               else
               {
                  /* points pSchedDetailData to the beginning of 
SCHED_DETAIL_DATA */
                  pSchedDetailData =  
                     (SCHED_DETAIL_DATA *) ( (char *)pSchedDetailEntry+ 
pSchedDetailEntry->wOffsetDetails );                                
                  /* loops through all the SCHED_DETAIL_DATA for this 
SCHED_DETAIL_ENTRY */
                  for (DWORD iData = 0; iData < wItemCount; iData++ )
                  {
                     printf("   * SCHED_DETAIL_DATA %d\n",iData); 
                     /* .
                        .
                        - - -  you can print SCHED_DETAIL_DATA header 
information here - - -
                     */

                     if ( pSchedDetailData->wDataLen ) {
                              /* .
                                 .
                                 now you can print SCHED_DETAIL_DATA : 
                                    the starting point would be 
pSchedDetailData + sizeof(SCHED_DETAIL_DATA)
                                    the length would be 
pSchedDetailData->wDataLen
	                 */
                     }
                     /* points to the next SCHED_DETAIL_DATA */
                pSchedDetailData = (SCHED_DETAIL_DATA *) ( (char *) 
pSchedDetailData + 
                                        pSchedDetailData->wDataLen + 
                                        sizeof(BYTE) +
                                        sizeof(WORD) +
                                        sizeof(WORD) );
                   }
               }

               /* moves pointer to point to the next SCHED_DETAIL_ENTRY */
               pSchedDetailEntry = (SCHED_DETAIL_ENTRY *) ( (char *) 
pSchedDetailEntry + pSchedDetailEntry->wEntryLen);

	 }  /* for (DWORD iEntry = 0; iEntry < pList->wNumEntries; iEntry++) */

```

**See Also :**
[LIST](/domino-c-api-docs/reference/Data/LIST)
[SCHED_DETAIL_DATA](/domino-c-api-docs/reference/Data/SCHED_DETAIL_DATA)
[SCHED_DETAIL_ENTRY](/domino-c-api-docs/reference/Data/SCHED_DETAIL_ENTRY)
[SCHED_DETAIL_LIST_ATTR_xxx](/domino-c-api-docs/reference/Symb/SCHED_DETAIL_LIST_ATTR_xxx)
---
