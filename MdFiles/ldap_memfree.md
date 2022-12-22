




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



**ldap\_memfree** **- Free
allocated LDAP memory**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



void
LNPUBLIC **ldap\_memfree(**  

      char \*ptr**);**



**Description :**



This
function frees the memory allocated by the LDAP library.


 


Implemented
as a macro:


 


#define
ldap\_memfree(ptr)   ND\_ldap\_memfree((ptr))


 


**Parameters :**



Input :  

ptr  -  A pointer to memory allocated by the LDAP library, such as the  
attribute type names returned by ldap\_first\_attribute and ldap\_next\_attribute,
or the DN returned by ldap\_get\_dn.  If ptr is NULL, the ldap\_memfree call does
nothing.  

  




 


 **Sample Usage :**



    for ( e
= ldap\_first\_entry( ld, result ); e != NULL;


          e
= ldap\_next\_entry( ld, e ) )


    {


         if
( (sdn = ldap\_get\_dn( ld, e )) != NULL )


         {


            
printf( "\tdn: %s\n", sdn );


            
ldap\_memfree( sdn );


         }


        
for ( a = ldap\_first\_attribute( ld, e, &ber );


              
a != NULL; a = ldap\_next\_attribute( ld, e, ber ) )


         {


            
if ((vals = ldap\_get\_values( ld, e, a)) != NULL )


            
{


                
for ( j = 0; vals[j] != NULL; j++ )


                
{


                    
printf( "\t%s: %s\n", a, vals[j] );


                
}


                 ldap\_value\_free(
vals );


            
}


            
ldap\_memfree(a);


         }


        
ber\_free(ber, 0);


    }


   
ldap\_msgfree( result );  

  




 **See Also :**


**[ldap\_first\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59B5D64DDCE3D2C085256F5C00488A67)**


**[ldap\_get\_dn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BDD0B880523CEAF385256F5C00488A63)**


**[ldap\_next\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1DC5BFBCDAA429A685256F5C00488A68)**



----------------------------------------------------------------------------------------------------------


 





