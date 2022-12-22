




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



**Function : LDAP**



**ldap\_compare\_ext\_s** **-
Synchronous compare attribute value assertion with controls.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_compare\_ext\_s(**  

      LDAP \*ld,  

      const char \*dn,  

      const char \*attr,  

      const struct berval \*bvalue,  

      LDAPControl \*\*sctrls,  

      LDAPControl \*\*cctrls**);**



**Description :**



This
function will do a synchronous compare attribute value assertion, with
controls, against an LDAP entry.


 


Implemented
as a macro:


 


#define
ldap\_compare\_ext\_s(ld, dn, attr, bvalue, sctrl, cctrl)\


             
ND\_ldap\_compare\_ext\_s((ld), (dn), (attr), (bvalue), (sctrl), (cctrl))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

dn  -  The distinguished name of the entry to compare against.  

  

attr  -  The attribute to compare against.  

  

bvalue  -  The attribute value to compare against those found in the given
entry. This is a pointer to a struct berval so it is possible to compare binary
values.  

  

sctrls  -  Pointer to a list of LDAP server controls.  NULL if no server
controls are to be used.  

  

cctrls  -  Pointer to a list of LDAP client controls.  NULL if no client
controls are to be used.  

  




Output :  

(routine)  -  LDAP\_COMPARE\_TRUE, LDAP\_COMPARE\_FALSE  - If the operation was
successful, or another LDAP result code if not.  

  

  




 **Sample Usage :**



    /\*
compare the value "person" against the objectclass attribute \*/


   
printf("\n  Comparison results:\n\n");


 


   
compAttribute = "objectclass";


   
compValue = "person";


   
bvalue.bv\_val = compValue;


   
bvalue.bv\_len = strlen(compValue);


 


    rc =
ldap\_compare\_ext\_s( ld, DN, compAttribute, &bvalue, NULL, NULL );


    switch
( rc )


    {


        
case LDAP\_COMPARE\_TRUE:


            
printf( "\tThe value \"person\" is contained in the objectclass
"


                    
"attribute.\n" );


            
break;


        
case LDAP\_COMPARE\_FALSE:


            
printf( "\tThe value \"person\" is not contained in the
objectclass "


                    
"attribute.\n" );


            
break;


        
default:


            
ldap\_perror( ld, "ldap\_compare\_s" );


    }


 


    /\*
compare the value "xyzzy" against the objectclass attribute \*/


   
compValue = "xyzzy";


   
bvalue.bv\_val = compValue;


   
bvalue.bv\_len = strlen(compValue);


 


    rc =
ldap\_compare\_ext\_s( ld, DN, compAttribute, &bvalue, NULL, NULL );


    switch
( rc )


    {


        
case LDAP\_COMPARE\_TRUE:                            


            
printf( "\tThe value \"xyzzy\" is contained in the objectclass
"


                    
"attribute.\n" );


             break;


        
case LDAP\_COMPARE\_FALSE:


            
printf( "\tThe value \"xyzzy\" is not contained in the
objectclass "


                    
"attribute.\n" );


            
break;


        
default:


            
ldap\_perror( ld, "ldap\_compare\_s" );


    }


 




----------------------------------------------------------------------------------------------------------


 





