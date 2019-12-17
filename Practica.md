# Usuarios, grupos y ACLs en LDAP

### Creación de usuarios
Se van a crear 10 usuarios con nombres en LDAP. Serán objetos de tipo posixAccount e inetOrgPerson con un atributo userPassword.

Se buscan los atributos que contienen las clases [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount) e [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson), además de los demás objectClass que serán necesarios para el ejercicio. Se va a usar la página [zytrax](https://www.zytrax.com/books/ldap/ape/) gracias a la cual, se va a crear un glosario con los principales objectClass y sus atributos [aquí](https://github.com/PalomaR88/LDAP/blob/master/glosario.md).

En primer lugar se crea la unidad organizativa usuarios que se añadirán a través del fichero unidadOrgPeople.ldif con los objectClass [top](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#top) y [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit):
~~~
dn: ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: organizationalUnit
ou: People
~~~

Se añade a LDAP:
~~~
debian@croqueta:~$ ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f unidadOrgPeople.ldif
Enter LDAP Password: 
adding new entry "ou=People,dc=paloma,dc=gonzalonazareno,dc=org"
~~~

Se crea el fichero usuarios.ldif dentro del cual se encuentra la información de los usuarios que se quieren añadir:
~~~
dn: uid=paloma,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn:: UGFsb21hIGRlbCBSb2PDrW8gR2FyY8OtYSBDYW1ww7NuCg==
uid: paloma
uidNumber: 2000
gidNumber: 2500
homeDirectory: /home/paloma
loginShell: /bin/bash
userPassword: {SSHA}+qOt08A0t3aCSWR8tuksmexgOhqKwf8z
mail: palomagarciacampon08@gmail.com
givenName: Paloma
sn:: R2FyY8OtYSBDYW1ww7NuCg==

dn: uid=alejandro,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Alejandro Morales Gracia
uid: alejandro
uidNumber: 2001
gidNumber: 2501
homeDirectory: /home/alejandro
loginShell: /bin/bash
userPassword: {SSHA}+qOt08A0t3aCSWR8tuksmexgOhqKwf8z
mail: moralg@gmail.com
givenName: Alejandro
sn: Morales

dn: uid=fernando,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Fernando Tirado Bulnes
uid: fernando
uidNumber: 2002
gidNumber: 2502
homeDirectory: /home/fernando
loginShell: /bin/bash
userPassword: {SSHA}PASEKAFIGNOcy2KxrzhtGq7NW9F9EhFo
mail: fernandotirado@gmail.com
givenName: Fernando
sn: Tirado

dn: uid=francisco,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Francisco de Goya
uid: francisco
uidNumber: 2003
gidNumber: 2503
homeDirectory: /home/francisco
loginShell: /bin/bash
userPassword: {SSHA}Kxl21nO+y0ZVxcuZMftNnmIlFf+W5NIV
mail: franciscoG@gmail.com
givenName: francisco
sn: Goya

dn: uid=pablo,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn:: UGFibG8gUnXDrXogUGljYXNzbwo=
uid: pablo
uidNumber: 2004
gidNumber: 2504
homeDirectory: /home/pablo
loginShell: /bin/bash
userPassword: {SSHA}Wm9ddk+VrbqDg0wnnyY9NNxzyo9FXVJU
mail: pabloPicasso@gmail.com
givenName: pablo
sn: Picasso

dn: uid=miguel,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Miguel Angel Buonaroti
uid: miguel
uidNumber: 2005
gidNumber: 2505
homeDirectory: /home/miguel
loginShell: /bin/bash
userPassword: {SSHA}hS9wbekVRiaxKCxbdqOS8903Q1zpcl6A
mail: miguelA@gmail.com
givenName: miguel
sn: Bounaroti

dn: uid=rafael,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Rafael de Sancio
uid: rafael
uidNumber: 2006
gidNumber: 2506
homeDirectory: /home/rafael
loginShell: /bin/bash
userPassword: {SSHA}i5tHsYfYE+1A3YpDBzQ/BR8CorIUNGdd
mail: rafaelSancio@gmail.com
givenName: rafael
sn: Sancio

dn: uid=remedios,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Remedios Baro
uid: ramedios
uidNumber: 2007
gidNumber: 2507
homeDirectory: /home/remedios
loginShell: /bin/bash
userPassword: {SSHA}91QjalZLUGdIRNJ+ijP+LQ28Vboz7Qsv
mail: remediosbaro@gmail.com
givenName: remedios
sn: Baro

dn: uid=frida,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: frida kahlo
uid: frida
uidNumber: 2008
gidNumber: 2508
homeDirectory: /home/frida
loginShell: /bin/bash
userPassword: {SSHA}6XFYhd/jYlav+hsRWNtH1pFgbP4RiM6U
mail: fridaK@gmail.com
givenName: frida
sn: Kahlo

dn: uid=diego,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
cn: Diego Rivera
uid: diego
uidNumber: 2009
gidNumber: 2509
homeDirectory: /home/diego
loginShell: /bin/bash
userPassword: {SSHA}EBF0d80V1psj1Mtx13KQaa7heBICmp+S
mail: diegoRivera@gmail.com
givenName: diego
sn: Rivera
~~~

Y se añaden los objetos usuarios:
~~~
debian@croqueta:~$ ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f usuarios.ldif 
~~~


### Crea 3 grupos en LDAP dentro de una unidad organizativa diferente que sean objetos del tipo groupOfNames. Estos grupos serán: comercial, almacen y admin

Se crea la unidad organizativa para los grupos creando el fichero unidadOrgGroup.ldif;
~~~
dn: ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: organizationalUnit
ou: Group
~~~

Se añade a LDAP:
~~~
debian@croqueta:~$ ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f unidadOrgGroup.ldif 
Enter LDAP Password: 
adding new entry "ou=Group,dc=paloma,dc=gonzalonazareno,dc=org"
~~~

Y se crea el fichero, grupos.ldif, de los objetos grupos:
~~~
dn: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: comercial
member:

dn: cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: almacen
member:

dn: cn=admin,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: admin
member:
~~~

Se agregan los grupos:
~~~
debian@croqueta:~$ ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f grupos.ldif 
~~~

### Añade usuarios que pertenezcan a:
- Solo al grupo comercial
- Solo al grupo almacen
- Al grupo comercial y almacen
- Al grupo admin y comercial
- Solo al grupo admin

Para ello se va a crear un fichero, grupousuarios.ldif
~~~
dn: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
replace: member
member: uid=paloma,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
replace: member
member: uid=alejandro,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
add: member
member: uid=fernando,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
add: member
member: uid=fernando,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=admin,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
replace: member
member: uid=francisco,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
add: member
member: uid=francisco,ou=People,dc=paloma,dc=gonzalonazareno,dc=org

dn: cn=admin,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
add: member
member: uid=pablo,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
~~~

Se agregan los cambios:
~~~
debian@croqueta:~$ ldapmodify -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f grupousuarios.ldif 
~~~

> Comprobación:
~~~
debian@croqueta:~$ ldapsearch -x -h croqueta -b ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
# extended LDIF
#
# LDAPv3
# base <ou=Group,dc=paloma,dc=gonzalonazareno,dc=org> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# Group, paloma.gonzalonazareno.org
dn: ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: organizationalUnit
ou: Group

# admin, Group, paloma.gonzalonazareno.org
dn: cn=admin,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: admin
member: uid=francisco
member: uid=pablo

# almacen, Group, paloma.gonzalonazareno.org
dn: cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: almacen
member: uid=alejanddro
member: uid=fernando

# comercial, Group, paloma.gonzalonazareno.org
dn: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: groupOfNames
cn: comercial
member: uid=paloma
member: uid=fernando
member: uid=francisco

# search result
search: 2
result: 0 Success

# numResponses: 5
# numEntries: 4
~~~


### Modifica OpenLDAP apropiadamente para que se pueda obtener los grupos a los que pertenece cada usuario a través del atributo "memberOf"

Se crea una serie de ficheros de configuración para añadir el módulo necesario para que aparezca el atributo memberOf.

El primero de ellos lo vamos a llamar memberof_config.lif. Para cargar el módulo memberof.la y configurarlo.
~~~
dn: cn=module,cn=config
cn: module
objectClass: olcModuleList
objectclass: top
olcModuleLoad: memberof.la
olcModulePath: /usr/lib/ldap

dn: olcOverlay={0}memberof,olcDatabase={1}mdb,cn=config
objectClass: olcConfig
objectClass: olcMemberOf
objectClass: olcOverlayConfig
objectClass: top
olcOverlay: memberof
olcMemberOfDangling: ignore
olcMemberOfRefInt: TRUE
olcMemberOfGroupOC: groupOfNames
olcMemberOfMemberAD: member
olcMemberOfMemberOfAD: memberOf
~~~

El segundo y el tercer fichero es para agregar y configurar la integridad referencial, es decir, hay que crear una relación entre los objetos grupos y usuarios y que estos no pierdan coherencia. 
~~~
dn: cn=module,cn=config
cn: module
objectclass: olcModuleList
objectclass: top
olcmoduleload: refint.la
olcmodulepath: /usr/lib/ldap

dn: olcOverlay={1}refint,olcDatabase={1}mdb,cn=config
objectClass: olcConfig
objectClass: olcOverlayConfig
objectClass: olcRefintConfig
objectClass: top
olcOverlay: {1}refint
olcRefintAttribute: memberof member manager owne
~~~

~~~
dn: olcOverlay=memberof,olcDatabase={1}mdb,cn=config
objectClass: olcOverlayConfig
objectClass: olcMemberOf
olcOverlay: memberof
olcMemberOfRefint: TRUE
~~~

Cargar los tres nuevos ficheros .ldif creados:
~~~
debian@croqueta:~$ sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f memberof_config.lif.ldif 
adding new entry "cn=module,cn=config"

adding new entry "olcOverlay={0}memberof,olcDatabase={1}mdb,cn=config"


debian@croqueta:~$ sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f refint1.ldif
adding new entry "cn=module,cn=config"

adding new entry "olcOverlay={1}refint,olcDatabase={1}mdb,cn=config"

sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f refint2.ldif
  adding new entry "olcOverlay={1}refint,olcDatabase={1}hdb,cn=config"
  ldap_add: No such object (32)
  	matched DN: cn=config
~~~

> Para que los cambios en se realicen sobre los grupos ya creados se deben eliminar estos objetos y volver a crearlos.
~~~
debian@croqueta:~$ sudo ldapdelete -x -D "cn=admin,dc=paloma,dc=gonzalonazareno,dc=org" 'cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org' -WEnter LDAP Password: 
debian@croqueta:~$ sudo ldapdelete -x -D "cn=admin,dc=paloma,dc=gonzalonazareno,dc=org" 'cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org' -WEnter LDAP Password: 
debian@croqueta:~$ sudo ldapdelete -x -D "cn=admin,dc=paloma,dc=gonzalonazareno,dc=org" 'cn=admin,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org' -W
Enter LDAP Password: 
~~~

Y se vuelve a añadir el fichero grupos.ldif y las modificaciones de los grupos, con la relación entre los grupos y los usuarios, que se había guardado en el fichero gruposusuarios.ldif.

Comprobación. Como memberOf no es parte de la configuración básica de LDAP, para que aparezca al realizar una búsqueda hay que especificar que éste aparezca:
~~~
debian@croqueta:~$ ldapsearch -LL -Y EXTERNAL -H ldapi:/// "(uid=fernando)" -b dc=paloma,dc=gonzalonazareno,dc=org memberOf
SASL/EXTERNAL authentication started
SASL username: gidNumber=1000+uidNumber=1000,cn=peercred,cn=external,cn=auth
SASL SSF: 0
version: 1

dn: uid=fernando,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
memberOf: cn=comercial,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
memberOf: cn=almacen,ou=Group,dc=paloma,dc=gonzalonazareno,dc=org
~~~

### Crea las ACLs necesarias para que los usuarios del grupo almacen puedan ver todos los atributos de todos los usuarios pero solo puedan modificar las suyas

La sintaxis para crear ACLs es la siguiente:
~~~
access to <qué> [by <quién> [<acceso>] [<control>]]
~~~

Y los priviledios son:
- none          0       sin acceso
- disclose      d       necesario para información en caso de error
- auth          dx 	    necesario para autenticación (bind)
- compare       cdx     necesario para comparar
- search        scdx    necesario para aplicar los filtros de búsqueda
- read          rscdx   necesario para leer los resultados de la búsqueda
- add|delete}   wrscdx 	necesario para modifica
- manage        mwrscdx necesario para gestionar 


access to People by People, memberof=almacen read

### Crea las ACLs necesarias para que los usuarios del grupo admin puedan ver y modificar cualquier atributo de cualquier objeto


# LDAPs
### Configura el servidor LDAP de croqueta para que utilice el protocolo ldaps:// a la vez que el ldap:// utilizando el certificado x509 de la práctica de https o solicitando el correspondiente a través de gestiona.

### Realiza las modificaciones adecuadas en el cliente ldap de croqueta para que todas las consultas se realicen por defecto utilizando ldaps://

