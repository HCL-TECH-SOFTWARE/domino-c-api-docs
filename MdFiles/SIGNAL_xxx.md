




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




 


**Symbolic Value : Views**



**SIGNAL\_xxx** **-** NIFReadEntries()
- retSignalFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      SIGNAL\_DEFN\_ITEM\_MODIFIED     -  At least one of the
"definition" view items (Selection formula or sorting rules) has been
modified by another user since the last NIFReadEntries. Upon receipt, you may
wish to re-read the view note if up-to-date copies of these items are needed.
You also may wish to re-synchronize your index position and re-read the rebuilt
index. This signal is returned only ONCE per detection.  

  

      SIGNAL\_VIEW\_ITEM\_MODIFIED     -  At least one of the
non-"definition" view items (View name,etc) has been modified since
the last NIFReadEntries. Upon receipt, you may wish to re-read the view note if
up-to-date copies of these items are needed. This signal is returned only ONCE
per detection.  

  

      SIGNAL\_INDEX\_MODIFIED              -  The collection index has been
modified by another user since the last NIFReadEntries. Upon receipt, you may
wish to re-synchronize your index position and re-read the modified index. This
signal is returned only ONCE per detection.  

  

      SIGNAL\_UNREADLIST\_MODIFIED   -  The unread list has been modified by
another window using the same HCOLLECTION context. Upon receipt, you may wish
to repaint the window if the window contains the state of the unread flags.  

  

      SIGNAL\_DATABASE\_MODIFIED      -  Collection is not up to date.  

  

      SIGNAL\_MORE\_TO\_DO       -  End of collection has not been reached because
the return buffer is too full. The NIFReadEntries call should be repeated to
continue reading the desired entries.  

  

      SIGNAL\_VIEW\_TIME\_RELATIVE     -  The view contains a time-relative
formula (e.g., @Now). Use this flag to tell if the collection will EVER be
up-to-date since time-relative views, by definition, are NEVER up-to-date.  

  

      SIGNAL\_NOT\_SUPPORTED            -  Returned if signal flags are not
supported. This is used by NIFFindByKeyExtended when it is talking to a pre-V4
server that does not support signal flags for FindByKey.  

  

      SIGNAL\_ANY\_CONFLICT     -  Mask that defines all sharing conflicts,
indicating that the database or collection has changed:  

(SIGNAL\_DEFN\_ITEM\_MODIFIED | SIGNAL\_VIEW\_ITEM\_MODIFIED | SIGNAL\_INDEX\_MODIFIED
| SIGNAL\_UNREADLIST\_MODIFIED | SIGNAL\_DATABASE\_MODIFIED)  

  

      SIGNAL\_ANY\_NONDATA\_CONFLICT          -  Mask that defines all
"sharing conflicts" except for SIGNAL\_DATABASE\_MODIFIED. This can be
used in combination with SIGNAL\_VIEW\_TIME\_RELATIVE to tell if the database or
collection has truly changed out from under the user or if the view is a
time-relative view which will NEVER be up-to-date. SIGNAL\_DATABASE\_MODIFIED is
always returned for a time-relative view to indicate that it is never
up-to-date:  

(SIGNAL\_DEFN\_ITEM\_MODIFIED | \  

 SIGNAL\_VIEW\_ITEM\_MODIFIED | \  

 SIGNAL\_INDEX\_MODIFIED | \  

 SIGNAL\_UNREADLIST\_MODIFIED)  

  

      SIGNAL\_DIFF\_READ\_NOT\_DONE   -  If a differential view read was requested
by providing DiffTime but it could not be performed for some reason, a
"regular" ReadEntries is done then this flag is set.  

  




**Description :**



NIFReadEntries()
returns these flags, as output, in the WORD specified by the retSignalFlags
parameter. NIFReadEntries() may set multiple signal flags in the SignalFlags
word by bitwise Or-ing the individual flag values together.  

  

If NIFReadEntries() sets one of the  flags represented by SIGNAL\_ANY\_CONFLICT,
the collection has changed since it was last read. Your program may respond to
this signal by updating the collection with NIFUpdateCollection(), resetting
the COLLECTIONPOSITION, and calling NIFReadEntries() again.  

  

If NIFReadEntries() sets the SIGNAL\_MORE\_TO\_DO flag, then the end of the
collection has not been reached and there exists more information than could
fit in the return buffer.  Your program may respond to this signal by calling
NIFReadEntries  again to retrieve an additional buffer of information.


 **Sample Usage :**


   do  

   {  

      if ( error = NIFReadEntries(  

             hCollection,&CollPosition,NAVIGATE\_NEXT,  

             1L,NAVIGATE\_NEXT,0xFFFFFFFF, READ\_MASK\_NOTEID,  

             &hBuffer, NULL, NULL, &EntriesFound,  

             &SignalFlag))       /\* share warning signal flag \*/  

      {  

         return (ERR(error));  

      }  

  

      if (hBuffer == NULLHANDLE)  

      {  

         return (NOERROR);  

      }  

  

      IdList = (NOTEID \*) OSLockObject (hBuffer);  

  

      for (i=0; i<EntriesFound; i++)  

      {  

         ProcessOneEntry(IdList[i]);   

      }  

  

      OSUnlockObject (hBuffer);  

      OSMemFree (hBuffer);  

  

   }  while (SignalFlag & SIGNAL\_MORE\_TO\_DO);


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**


**[NIFUpdateCollection](NIFUpdateCollection.md)**



----------------------------------------------------------------------------------------------------------


 





