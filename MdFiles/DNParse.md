




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




 


**Function : Distinguished Name**



**DNParse** **- Parses a
distinguished name into standard components.**


**----------------------------------------------------------------------------------------------------------**



**#include <dname.h>**



STATUS
LNPUBLIC **DNParse(**  

      DWORD  Flags,  

      const char far \*TemplateName,  

      const char far \*InName,  

      DN\_COMPONENTS far \*Comp,  

      WORD  CompSize**);**



**Description :**



This
function parses a distinguished name into its standard components.


 


An
escape mechanism is provided to allow the '=' and the '/' characters to occur
in the value of one of the components of the name by preceding the character
with the '$' character.  


 


Below
are some examples of the components returned in DN\_COMPONENTS by DNParse given
the specified InName parameter.


 


**InName:          "/C=GB/A=RN/P=Red Squadron/O=CAM/CN=Jayne
Doe@FooDomain"**


DN\_COMPONENTS:


      Flags: 
                                                      DN\_NONABBREV


      Country
Name:                                            "GB"


      Org
Name:                                                  "CAM"


      Org
Unit:


      Common
Name:                                          "Jayne Doe"


      Domain:                                                      "FooDomain"


      Private
Management Domain:                      "Red Squadron"


      Administration
Management Domain:           "RN"


      Given
Name:


      Surname:


      Initials:


      Generational
Qualifier:


      Internet
Address Phrase Part:


      Internet
Address Local Part:                         "/C=GB/A=RN/P=Red
Squadron/O=CAM/CN=Jayne Doe"                    


      Internet
Address Route:


      Internet
Address Comment:


      Route
address or 822 Simple Address:         "/C=GB/A=RN/P=Red
Squadron/O=CAM/CN=Jayne Doe@FooDomain"


      Hierarchy
Only:


      LDAP
uid:


      Locality:


 


**InName:         "/C=GB/A=RN/P=Red
Squadron/O=CAM/S=Doe/G=Jayne"**


DN\_COMPONENTS:


      Flags: 
                                                      DN\_NONABBREV


      Country
Name:                                            "GB"


      Org
Name:                                                  "CAM"


      Org
Unit:


      Common
Name:                                          


      Domain:                                                      


      Private
Management Domain:                      "Red Squadron"


      Administration
Management Domain:           "RN"


      Given
Name:                                               "Jayne"


      Surname:                                                    "Doe"


      Initials:


      Generational
Qualifier:


      Internet
Address Phrase Part:


      Internet
Address Local Part:                         "/C=GB/A=RN/P=Red
Squadron/O=CAM/CN=Jayne Doe"                    


      Internet
Address Route:


      Internet
Address Comment:


      Route
address or 822 Simple Address:         "/C=GB/A=RN/P=Red
Squadron/O=CAM/CN=Jayne Doe@FooDomain"


      Hierarchy
Only:


      LDAP
uid:


      Locality:


 


**InName:    "Jayne Doe <jdoe@lotus.com>"**


DN\_COMPONENTS:


      Flags: 
                                                      DN\_NONDISTINGUISHED


      Country
Name:                                            


      Org
Name:                                                  


      Org
Unit:


      Common
Name:                                          "Jayne Doe"


      Domain:                                                      "lotus.com"


      Private
Management Domain:                      


      Administration
Management Domain:           


      Given
Name:


      Surname:


      Initials:


      Generational
Qualifier:


      Internet
Address Phrase Part:                      "Jayne Doe


      Internet
Address Local Part:                         "jdoe"   


      Internet
Address Route:


      Internet
Address Comment:


      Route
address or 822 Simple Address:         "jdoe@lotus.com"


      Hierarchy
Only:


      LDAP
uid:


      Locality:


 


**InName:          "Jayne Doe/Sales$/Marketing/Lotus/GB"**


DN\_COMPONENTS:


      Flags: 
                                                      0


      Country
Name:                                            "GB"


      Org
Name:                                                  "Lotus"


      Org
Unit:                                                    Sales$/Marketing


      Common
Name:                                          "Jayne Doe"


      Domain:                                                      


      Private
Management Domain:                      


      Administration
Management Domain:           


      Given
Name:


      Surname:


      Initials:


      Generational
Qualifier:


      Internet
Address Phrase Part:


      Internet
Address Local Part:                                     


      Internet
Address Route:


      Internet
Address Comment:


      Route
address or 822 Simple Address:         


      Hierarchy
Only:                                           Sales$/Marketing/Lotus/GB


      LDAP
uid:


      Locality:


 


 


**Parameters :**



Input :  

Flags  -  Reserved for future use.  Always pass in 0L for this argument.  

  

TemplateName  -  Currently not supported.  Always pass in NULL for this
argument.  

  

InName  -   Pointer to the null terminated distinguished name that is to be
parsed.  

  

CompSize  -  Size of the buffer (DN\_COMPONENTS structure) that the Comp
parameter points to.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_DN\_COMP\_VERSION - CompSize parameter is an invalid value.  

  

ERR\_xxx - Error returned by lower level functions.  Call OSLoadString to
interpret the code.  

  

  

Comp  -  Pointer to a DN\_COMPONENTS structure.  The structure contains the
returned components of the InName parameter.  

  




 **Sample Usage :**


  

char InName[MAXUSERNAME];    /\* InName \*/


   char
Tmp[MAXUSERNAME];  

DN\_COMPONENTS DNComp;     

short i;


    STATUS error;  

  

/\* ... \*/  

  

   error = DNParse(0L, NULL, InName, &DNComp, sizeof(DNComp));  

   if (error)                                                    

      return (error);                                            

                                                              

   printf ("\n\nDN\_COMPONENTS for %s\n", InName);


             

   printf ("Flags:  %lu\n", DNComp.Flags);


                       

   strncpy(Tmp, DNComp.C, DNComp.CLength);                       

   Tmp[DNComp.CLength] = '\0';                                   

   printf ("Country Name:  %s\n", Tmp); 


                         

   strncpy(Tmp, DNComp.O, DNComp.OLength);                       

   Tmp[DNComp.OLength] = '\0';                                   

   printf ("Org Name:  %s\n", Tmp);  


                         
  

   for ( i = 0; i < DN\_OUNITS, DNComp.OULength[i]; i++)          

   {                                                             

      strncpy (Tmp, DNComp.OU[i], DNComp.OULength[i]);           

      Tmp[DNComp.OULength[i]] = '\0';                            

      printf ("Org Unit Name:  %s\n", Tmp);                      

   }       


                                                   
  

   strncpy(Tmp, DNComp.CN, DNComp.CNLength);                     

   Tmp[DNComp.CNLength] = '\0';                                  

   printf ("Common Name:  %s\n", Tmp); 


                       
  

   strncpy(Tmp, DNComp.Domain, DNComp.DomainLength);  

   Tmp[DNComp.DomainLength] = '\0';           

   printf ("Domain:  %s\n",DNComp.Domain);


 


     
strncpy(Tmp, DNComp.PRMD, DNComp.PRMDLength);  

      Tmp[DNComp.PRMDLength] = '\0';  

      printf ("Private management domain:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.ADMD, DNComp.ADMDLength);  

      Tmp[DNComp.ADMDLength] = '\0';  

      printf ("Administration management domain:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.G, DNComp.GLength);  

      Tmp[DNComp.GLength] = '\0';  

      printf ("Given Name:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.S, DNComp.SLength);  

      Tmp[DNComp.SLength] = '\0';  

      printf ("Surname:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.I, DNComp.ILength);  

      Tmp[DNComp.ILength] = '\0';  

      printf ("Initials:  %s\n", Tmp);


     
strncpy(Tmp, DNComp.Q, DNComp.QLength);  

      Tmp[DNComp.QLength] = '\0';  

      printf ("Generational qualifier:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.Phrase, DNComp.PhraseLength);  

      Tmp[DNComp.PhraseLength] = '\0';  

      printf ("Internet Address Phrase Part:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.LP, DNComp.LPLength);  

      Tmp[DNComp.LPLength] = '\0';  

      printf ("Internet Address Local Part:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.R, DNComp.RLength);  

      Tmp[DNComp.RLength] = '\0';  

      printf ("Internet Address Route:  %s\n", Tmp);


 


      for (
i = 0; i < DN\_MAX\_COMMENTS, DNComp.CMTLength[i]; i++)  

      {  

         strncpy (Tmp, DNComp.CMT[i], DNComp.CMTLength[i]);  

         Tmp[DNComp.CMTLength[i]] = '\0';  

         printf ("Internet Address Comment:  %s\n", Tmp);  

      }


 


      strncpy(Tmp,
DNComp.Address821, DNComp.Address821Length);  

      Tmp[DNComp.Address821Length] = '\0';  

      printf ("Route Address or simple address portion:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.HierarchyOnly, DNComp.HierarchyOnlyLength);  

      Tmp[DNComp.HierarchyOnlyLength] = '\0';  

      printf ("Hierarchy Only:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.UID, DNComp.UIDLength);  

      Tmp[DNComp.UIDLength] = '\0';  

      printf ("LDAP uid:  %s\n", Tmp);


 


     
strncpy(Tmp, DNComp.L, DNComp.LLength);  

      Tmp[DNComp.LLength] = '\0';  

      printf ("Locality:  %s\n", Tmp);


 


   /\* ... \*/


 **See Also :**


**[DNAbbreviate](DNAbbreviate.md)**


**[DNCanonicalize](DNCanonicalize.md)**


**[DN\_COMPONENTS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/24D9907B9ECC4FFF8525667700438CC1)**



----------------------------------------------------------------------------------------------------------


 





