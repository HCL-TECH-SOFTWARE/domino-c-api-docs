




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



**ldap\_next\_attribute** **- Get the
next of the attribute types returned with an entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*LNPUBLIC **ldap\_next\_attribute(**  

      LDAP \*ld,  

      LDAPMessage \*entry,  

      BerElement \*ber**);**



**Description :**



This
function is used to step through the list of attribute types returned with an
entry.


 


Implemented
as a macro:


 


#define
ldap\_next\_attribute(ld, entry, ber)     ND\_ldap\_next\_attribute((ld), (entry),
(ber))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

entry  -  The entry whose attributes are to be stepped through, as returned by
ldap\_first\_entry or ldap\_next\_entry.  

  

ber  -  The address of a pointer used internally to keep track of the current
position in the entry.   This pointer MAY be from previous calls to
lap\_first\_attribute and ldap\_next\_attribute to step through the entry's
attributes.    

  




Output :  

(routine)  -  A pointer to an allocated buffer containing the current attribute
name. The attribute type names returned are suitable for passing in a call to
ldap\_get\_values.  This SHOULD be freed when no longer in use by calling
ldap\_memfree.  

  

NULL  - If the end of the attributes is reached, or if there is an error, in
which case the error parameters in the session handle ld will be set to
indicate the error.  

  

  

ber  -  The address of a pointer used internally to keep track of the current
position in the entry.   This pointer MAY be passed in subsequent calls to
ldap\_next\_attribute to step through the entry's attributes.    

  

After a set of calls to ldap\_first\_attribute and ldap\_next\_attribute, if ptr is
non-NULL, it SHOULD be freed by calling ber\_free( ber, 0 ).  Note that it is
very important to pass the second parameter as 0 (zero) in this call, since the
buffer associated  

with the BerElement does not point to separately allocated memory.  

  




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


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**


**[ldap\_first\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59B5D64DDCE3D2C085256F5C00488A67)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**



----------------------------------------------------------------------------------------------------------


 





