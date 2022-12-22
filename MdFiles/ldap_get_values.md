




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



**ldap\_get\_values** **- Retrieve
the values of a given attribute.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*\*LNPUBLIC **ldap\_get\_values(**  

      LDAP \*ld,  

      LDAPMessage \*entry,  

      const char \*target**);**



**Description :**



This
function is used to retrieve the values of a given attribute from an entry and
is only suitable for use with non-binary character string data.


 


Note that
the values returned are dynamically allocated and SHOULD be freed by calling
ldap\_value\_free when no longer in use.


 


Implemented
as a macro:


 


#define
ldap\_get\_values(ld, entry, target)     ND\_ldap\_get\_values((ld), (entry),
(target))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

entry  -  The entry from which to retrieve values, as returned by
ldap\_first\_entry or ldap\_next\_entry.  

  

target  -  The attribute whose values are to be retrieved, as returned by
ldap\_first\_attribute or ldap\_next\_attribute, or a caller supplied string (e.g.,
"mail").  

  




Output :  

(routine)  -  A pointer to an allocated buffer containing the given attribute
values.  

  

NULL - If no values are found or if an error occurs.  

  

  




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


                
ldap\_value\_free( vals );


            
}


            
ldap\_memfree(a);


         }


        
ber\_free(ber, 0);


    }


   
ldap\_msgfree( result );


 


 **See Also :**


**[ldap\_count\_values](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/29F38EDCBE6F80EF85256F5C00488A6B)**


**[ldap\_count\_values\_len](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/27B12543FC81EB2685256F5C00488A6C)**


**[ldap\_first\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59B5D64DDCE3D2C085256F5C00488A67)**


**[ldap\_first\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0238B4B4403930DA85256F5C00488A5F)**


**[ldap\_get\_values\_len](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DF025868229D9A2E85256F5C00488A6A)**


**[ldap\_next\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1DC5BFBCDAA429A685256F5C00488A68)**


**[ldap\_next\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/838CF92EE872121885256F5C00488A60)**


**[ldap\_value\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/69925F36F6F9779185256F5C00488A6D)**


**[ldap\_value\_free\_len](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/62DB93799BBEA0EE85256F5C00488A6E)**



----------------------------------------------------------------------------------------------------------


 





