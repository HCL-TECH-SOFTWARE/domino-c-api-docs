




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




 


**Function : Notes/FX data**



**NIFCollectionUpToDate** **- Check
whether a collection is up to date.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



BOOL **NIFCollectionUpToDate(**  

      HCOLLECTION  hCollection**);**



**Description :**



Return a
flag indicating if a collection is up to date. If not, UpdateCollection should
be called.


 


**Parameters :**



Input :  

hCollection  -  per user collection handle context  

  




Output :  

(routine)  -  Return a flag indicating if the collection is up to date  

  

  




 **Sample Usage :**



            /\*
Presumes HCOLLECTION hCollection and TIMEDATE myLastModifiedTime \*/


            {


            STATUS           Status
= NOERROR;


            TIMEDATE       LastModifiedTime;


            BOOL              bIsUpdated = FALSE;


 


            bIsUpdated = FALSE;


 


            if
(NIFCollectionIsRemote(hCollection))


                        {


                        /\*          If
the collection is remote all we can do is call


                                    NIFUpdateCollection
and set bIsUpdated to TRUE.  This is because


                                    NIFCollectionUpToDate
and NIFGetLastModifiedTime are not


                                    client/server
transactions.  Note, NIFUpdateCollection will check


                                    if
the collection is up to date, and return immediately if it is. \*/


 


                        if (Status =
NIFUpdateCollection(hCollection))


                                    goto Done;


                        


                        bIsUpdated = TRUE;


                        }


            else


                        {


                        //          If
the collection is local, bring the collection up to date


                        //          relative
to the database.


 


                        if
(!NIFCollectionUpToDate(hCollection))


                                    {


                                    if (Status =
NIFUpdateCollection(hCollection))


                                                goto Done;


                                    }


 


                        //          See
if the collection has been updated since the last time we


                        //          checked.



 


                        NIFGetLastModifiedTime(hCollection,
&LastModifiedTime);


 


                        if
(TimeDateCompare(&LastModifiedTime, &myLastModifiedTime) > 0)


                                    {


                                    myLastModifiedTime=
LastModifiedTime;


                                    bIsUpdated = TRUE;


                                    }


                        }


 


Done:


 


            return Status;


            }


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





