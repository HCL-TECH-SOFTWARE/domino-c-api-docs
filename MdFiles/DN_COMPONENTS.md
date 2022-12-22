




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




 


**Data Type : Distinguished Name**



**DN\_COMPONENTS** **-** Components
of a distinguished name


**----------------------------------------------------------------------------------------------------------**



**#include
<dname.h>**



**Definition :**



typedef struct {  

   DWORD Flags;                     /\* Parsing flags \*/  

   WORD CLength;                    /\* Country name length \*/  

   char far \*C;                     /\* Country name pointer \*/  

   WORD OLength;                    /\* Organization name length \*/  

   char far \*O;                     /\* Organization name pointer \*/  

   WORD OULength[DN\_OUNITS];        /\* Org Unit name lengths  

                                       OULength[0] is rightmost org


                                      
unit \*/  

   char far \*OU[DN\_OUNITS];         /\* Org unit name pointers  

                                       OU[0] is rightmost org


                                      
unit \*/  

   WORD CNLength;                   /\* Common name length \*/  

   char far \*CN;                    /\* Common name pointer \*/  

   WORD DomainLength;               /\* Domain name length \*/  

   char far \*Domain;                /\* Domain name pointer \*/  

   WORD PRMDLength;                 /\* Private management domain


                                      
name length \*/  

   char far \*PRMD;                  /\* Private management domain


                          
            name pointer \*/  

   WORD ADMDLength;                 /\* Administration management


                                      
domain name length \*/  

   char far \*ADMD;                  /\* Administration management


                                    
  domain name pointer \*/  

   WORD GLength;                    /\* Given name length \*/  

   char far \*G;                     /\* Given name name pointer \*/  

   WORD SLength;                    /\* Surname length \*/  

   char far \*S;                     /\* Surname pointer \*/  

   WORD ILength;                    /\* Initials length \*/  

   char far \*I;                     /\* Initials pointer \*/  

   WORD QLength;                    /\* Generational qualifier


                                      
(e.g., Jr) length \*/  

   char far \*Q;                     /\* Generational qualifier


                                      
(e.g., Jr) pointer \*/  

  




/\*  Original V4
structure ended here.


   The following fields
were added in V5 \*/


 


   WORD PhraseLength;              
/\* Internet Address Phrase Part


                                      
length \*/  

   char far \*Phrase;                /\* Internet Address Phrase Part


                                      
pointer \*/  

   WORD LPLength;                   /\* Internet Address Local Part


                                      
length \*/  

   char far \*LP;                    /\* Internet Address Local Part


                                      
pointer \*/  

   WORD RLength;                    /\* Internet Address Route


                                      
length \*/  

   char far \*R;                     /\* Internet Address Route


                                      
pointer \*/  

   WORD CMTLength[DN\_MAX\_COMMENTS]; /\* Internet Address Comment


                        
              lengths \*/  

   char far \*CMT[DN\_MAX\_COMMENTS];  /\* Internet Address Comment


                                      
pointers \*/  

   WORD Address821Length;           /\* Route address OR simple


                                      
address portion of 822


                                      
style internet address


                                      
length \*/  

   char far \*Address821;            /\* Route address OR simple


                                      
address portion of 822


                                       style
internet address


                                      
pointer \*/  

   WORD HierarchyOnlyLength;        /\* Hierarchy only (all


                                      
components after CN)


                                   
   length \*/  

   char far \*HierarchyOnly;         /\* Hierarchy only (all


                                      
components after CN)


                                      
pointer \*/  

   char far \*UID;                   /\* LDAP/X.500 userid \*/


   WORD UIDLength;                 
/\* LDAP/X.500 userid length \*/


   char far
\*L;                     /\* LDAP/X.500 localityName \*/


   WORD
LLength;                    /\* LDAP/X.500 localityName


                                      
length \*/


   WORD
STLength;                   /\* LDAP/X.500


                                      
stateOrProvinceName


                                      
length \*/


   char far
\*ST;                    /\* LDAP/X.500


                                      
stateOrProvinceName \*/


   WORD
STREETLength;               /\* LDAP/X.500 streetAddress


                                      
length \*/


   char far
\*STREET;                /\* LDAP/X.500 streetAddress \*/


   WORD
DCLength[DN\_DCS];           /\* LDAP/X.500 domainComponent


                                      
length \*/


   char far
\*DC[DN\_DCS];            /\* LDAP/X.500 domainComponent\*/


   WORD
CN2Length;                  /\* LDAP/X.500 container type


                                      
commonName length \*/


   char far \*CN2;                  
/\* LDAP/X.500 container type


                                      
commonName \*/


   WORD
OUExtLength[DN\_OUS\_EXT];    /\* LDAP/X.500


                                      
organizationalUnit name


                                     
 lengths \*/


                                   
/\* OUExtLength[0] is rightmost


                                      
org unit, in addition to the


                                      
OULength[DN\_OUNITS] \*/


   char far
\*OUExt[DN\_OUS\_EXT];     /\* LDAP/X.500


                                      
organizationalUnit name


                                      
lengths \*/


                                   
/\* OUExt[0] is rightmost org


                                      
unit, in addition to the


                                       OU[DN\_OUNITS]
\*/


} DN\_COMPONENTS;


 


**Description :**



This
structure contains the components of a distinguished name.  


 


String
components are not null terminated.


 **See Also :**


**[DNParse](DNParse.md)**


**[DN\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0096005E00F9007785255EC6007F7139)**



----------------------------------------------------------------------------------------------------------


 





