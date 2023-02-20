##### Function : Distinguished Name
##### DNParse - Parses a distinguished name into standard components.
---
```
#include <dname.h>
STATUS LNPUBLIC DNParse(

	DWORD  Flags,
	const char far *TemplateName,
	const char far *InName,
	DN_COMPONENTS far *Comp,
	WORD  CompSize);
```
**Description :**

This function parses a distinguished name into its standard components.

An escape mechanism is provided to allow the '=' and the '/' characters to 
occur in the value of one of the components of the name by preceding the 
character with the '$' character.  

Below are some examples of the components returned in DN_COMPONENTS by DNParse 
given the specified InName parameter.

InName:   "/C=GB/A=RN/P=Red Squadron/O=CAM/CN=Jayne Doe@FooDomain"
DN_COMPONENTS:
	Flags:   DN_NONABBREV
	Country Name: "GB"
	Org Name: "CAM"
	Org Unit:
	Common Name: "Jayne Doe"
	Domain: "FooDomain"
	Private Management Domain: "Red Squadron"
	Administration Management Domain: "RN"
	Given Name:
	Surname:
	Initials:
	Generational Qualifier:
	Internet Address Phrase Part:
	Internet Address Local Part: "/C=GB/A=RN/P=Red Squadron/O=CAM/CN=Jayne 
Doe" 
	Internet Address Route:
	Internet Address Comment:
	Route address or 822 Simple Address: "/C=GB/A=RN/P=Red 
Squadron/O=CAM/CN=Jayne Doe@FooDomain"
	Hierarchy Only:
	LDAP uid:
	Locality:

InName:         "/C=GB/A=RN/P=Red Squadron/O=CAM/S=Doe/G=Jayne"
DN_COMPONENTS:
	Flags:   DN_NONABBREV
	Country Name: "GB"
	Org Name: "CAM"
	Org Unit:
	Common Name: 
	Domain: 
	Private Management Domain: "Red Squadron"
	Administration Management Domain: "RN"
	Given Name: "Jayne"
	Surname: "Doe"
	Initials:
	Generational Qualifier:
	Internet Address Phrase Part:
	Internet Address Local Part: "/C=GB/A=RN/P=Red Squadron/O=CAM/CN=Jayne 
Doe" 
	Internet Address Route:
	Internet Address Comment:
	Route address or 822 Simple Address: "/C=GB/A=RN/P=Red 
Squadron/O=CAM/CN=Jayne Doe@FooDomain"
	Hierarchy Only:
	LDAP uid:
	Locality:

InName:   "Jayne Doe <jdoe@lotus.com>"
DN_COMPONENTS:
	Flags:   DN_NONDISTINGUISHED
	Country Name: 
	Org Name: 
	Org Unit:
	Common Name: "Jayne Doe"
	Domain: "lotus.com"
	Private Management Domain: 
	Administration Management Domain: 
	Given Name:
	Surname:
	Initials:
	Generational Qualifier:
	Internet Address Phrase Part: "Jayne Doe
	Internet Address Local Part: "jdoe" 
	Internet Address Route:
	Internet Address Comment:
	Route address or 822 Simple Address: "jdoe@lotus.com"
	Hierarchy Only:
	LDAP uid:
	Locality:

InName:   "Jayne Doe/Sales$/Marketing/Lotus/GB"
DN_COMPONENTS:
	Flags:   0
	Country Name: "GB"
	Org Name: "Lotus"
	Org Unit: Sales$/Marketing
	Common Name: "Jayne Doe"
	Domain: 
	Private Management Domain: 
	Administration Management Domain: 
	Given Name:
	Surname:
	Initials:
	Generational Qualifier:
	Internet Address Phrase Part:
	Internet Address Local Part:  
	Internet Address Route:
	Internet Address Comment:
	Route address or 822 Simple Address: 
	Hierarchy Only: Sales$/Marketing/Lotus/GB
	LDAP uid:
	Locality:


**Parameters :**
Input :
Flags  -  Reserved for future use.  Always pass in 0L for this argument.

TemplateName  -  Currently not supported.  Always pass in NULL for this argument.

InName  -   Pointer to the null terminated distinguished name that is to be parsed.

CompSize  -  Size of the buffer (DN_COMPONENTS structure) that the Comp parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_DN_COMP_VERSION - CompSize parameter is an invalid value.

ERR_xxx - Error returned by lower level functions.  Call OSLoadString to interpret the code.


Comp  -  Pointer to a DN_COMPONENTS structure.  The structure contains the returned components of the InName parameter.


**Sample Usage :**
```

char InName[MAXUSERNAME];    /* InName */
   char Tmp[MAXUSERNAME];
DN_COMPONENTS DNComp;   
short i;
	STATUS error;

/* ... */

   error = DNParse(0L, NULL, InName, &DNComp, sizeof(DNComp));
   if (error)                                                  
      return (error);                                          
                                                            
   printf ("\n\nDN_COMPONENTS for %s\n", InName);
           
   printf ("Flags:  %lu\n", DNComp.Flags);
                     
   strncpy(Tmp, DNComp.C, DNComp.CLength);                     
   Tmp[DNComp.CLength] = '\0';                                 
   printf ("Country Name:  %s\n", Tmp); 
                       
   strncpy(Tmp, DNComp.O, DNComp.OLength);                     
   Tmp[DNComp.OLength] = '\0';                                 
   printf ("Org Name:  %s\n", Tmp);  
                          
   for ( i = 0; i < DN_OUNITS, DNComp.OULength[i]; i++)        
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

      for ( i = 0; i < DN_MAX_COMMENTS, DNComp.CMTLength[i]; i++)
      {
         strncpy (Tmp, DNComp.CMT[i], DNComp.CMTLength[i]);
         Tmp[DNComp.CMTLength[i]] = '\0';
         printf ("Internet Address Comment:  %s\n", Tmp);
      }

      strncpy(Tmp, DNComp.Address821, DNComp.Address821Length);
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

   /* ... */
```
**See Also :**
[DNAbbreviate](/reference/Func/DNAbbreviate)
[DNCanonicalize](/reference/Func/DNCanonicalize)
[DN_COMPONENTS](/reference/Data/DN_COMPONENTS)
---
