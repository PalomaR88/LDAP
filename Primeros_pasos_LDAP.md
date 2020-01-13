
# Primeros pasos en LDAP
### Instalación 

Instalación del servidor:
~~~
vagrant@servidor:~$ sudo apt update
vagrant@servidor:~$ sudo apt upgrade
vagrant@servidor:~$ sudo apt install slapd ldap-utils 

     ┌────────────────────┤ Configuring slapd ├─────────────────────┐
     │ Please enter the password for the admin entry in your LDAP   │ 
     │ directory.                                                   │ 
     │                                                              │ 
     │ Administrator password:                                      │ 
     │                                                              │ 
     │ *********___________________________________________________ │ 
     │                                                              │ 
     │                            <Ok>                              │ 
     │                                                              │ 
     └──────────────────────────────────────────────────────────────┘ 

  ┌───────────────────────┤ Configuring slapd ├────────────────────────┐
  │ Please enter the admin password for your LDAP directory again to   │ 
  │ verify that you have typed it correctly.                           │ 
  │                                                                    │ 
  │ Confirm password:                                                  │ 
  │                                                                    │ 
  │ *********_________________________________________________________ │ 
  │                                                                    │ 
  │                               <Ok>                                 │ 
  │                                                                    │ 
  └────────────────────────────────────────────────────────────────────┘ 
~~~

Ver las primeras entradas:
~~~
vagrant@servidor:~$ sudo slapcat
dn: dc=nodomain
objectClass: top
objectClass: dcObject
objectClass: organization
o: nodomain
dc: nodomain
structuralObjectClass: organization
entryUUID: ec4acb2a-afc6-1039-9d57-5bb29650756c
creatorsName: cn=admin,dc=nodomain
createTimestamp: 20191210183045Z
entryCSN: 20191210183045.021571Z#000000#000#000000
modifiersName: cn=admin,dc=nodomain
modifyTimestamp: 20191210183045Z

dn: cn=admin,dc=nodomain
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e1NTSEF9ODNlTFNxTjZSL1FlTDNZUURtbHV6WkE2MmZuVDZvQlQ=
structuralObjectClass: organizationalRole
entryUUID: ec4b8448-afc6-1039-9d58-5bb29650756c
creatorsName: cn=admin,dc=nodomain
createTimestamp: 20191210183045Z
entryCSN: 20191210183045.026463Z#000000#000#000000
modifiersName: cn=admin,dc=nodomain
modifyTimestamp: 20191210183045Z
~~~

Para ver las entradas de LDAP:
~~~
vagrant@servidor:~$ ldapsearch -x -h localhost
# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1
~~~

### Configuración inicial

Configuración de LDAP:
~~~
vagrant@servidor:~$ sudo dpkg-reconfigure -plow slapd
~~~

Pregunta si se quiere omitir la configuración del servidor OpenLDAP. Se selecciona no.
~~~
  ┌───────────────────────┤ Configuring slapd ├───────────────────────┐
  │                                                                   │ 
  │ If you enable this option, no initial configuration or database   │ 
  │ will be created for you.                                          │ 
  │                                                                   │ 
  │ Omit OpenLDAP server configuration?                               │ 
  │                                                                   │ 
  │                  <Yes>                     <No>                   │ 
  │                                                                   │ 
  └───────────────────────────────────────────────────────────────────┘ 
~~~

Como se ha seleccionado no, pregunta el nombre de dominio:
~~~
  ┌───────────────────────┤ Configuring slapd ├────────────────────────┐
  │ The DNS domain name is used to construct the base DN of the LDAP   │ 
  │ directory. For example, 'foo.example.org' will create the          │ 
  │ directory with 'dc=foo, dc=example, dc=org' as base DN.            │ 
  │                                                                    │ 
  │ DNS domain name:                                                   │ 
  │                                                                    │ 
  │ paloma.gonzalonazareno.org________________________________________ │ 
  │                                                                    │ 
  │                               <Ok>                                 │ 
  │                                                                    │ 
  └────────────────────────────────────────────────────────────────────┘ 
~~~

Pide el nombre de la organización:
~~~
 ┌────────────────────────┤ Configuring slapd ├────────────────────────┐
 │ Please enter the name of the organization to use in the base DN of  │ 
 │ your LDAP directory.                                                │ 
 │                                                                     │ 
 │ Organization name:                                                  │ 
 │                                                                     │ 
 │ IES Gonzalo Nazareno_______________________________________________ │ 
 │                                                                     │ 
 │                               <Ok>                                  │ 
 │                                                                     │ 
 └─────────────────────────────────────────────────────────────────────┘ 
~~~

De nuevo pide una contraseña de administrador y su confirmación:
~~~
  ┌───────────────────────┤ Configuring slapd ├────────────────────────┐
  │ Please enter the admin password for your LDAP directory again to   │ 
  │ verify that you have typed it correctly.                           │ 
  │                                                                    │ 
  │ Confirm password:                                                  │ 
  │                                                                    │ 
  │ *********_________________________________________________________ │ 
  │                                                                    │ 
  │                               <Ok>                                 │ 
  │                                                                    │ 
  └────────────────────────────────────────────────────────────────────┘ 
~~~

Se indica el motor de base de datos. Por defecto es MDB:
~~~
┌────────────────────────┤ Configuring slapd ├────────────────────────┐
 │ HDB and BDB use similar storage formats, but HDB adds support for   │ 
 │ subtree renames. Both support the same configuration options.       │ 
 │                                                                     │ 
 │ The MDB backend is recommended. MDB uses a new storage format and   │ 
 │ requires less configuration than BDB or HDB.                        │ 
 │                                                                     │ 
 │ In any case, you should review the resulting database               │ 
 │ configuration for your needs. See                                   │ 
 │ /usr/share/doc/slapd/README.Debian.gz for more details.             │ 
 │                                                                     │ 
 │ Database backend to use:                                            │ 
 │                                                                     │ 
 │                                BDB                                  │ 
 │                                HDB                                  │ 
 │                                MDB                                  │ 
 │                                                                     │ 
 │                                                                     │ 
 │                               <Ok>                                  │ 
 │                                                                     │ 
 └─────────────────────────────────────────────────────────────────────┘ 
~~~

Pregunta si se quiere eliminar el directorio slapd de la base de datos . En nuestro caso, se indica no.
~~~
    ┌─────────────────────┤ Configuring slapd ├─────────────────────┐
    │                                                               │ 
    │                                                               │ 
    │                                                               │ 
    │ Do you want the database to be removed when slapd is purged?  │ 
    │                                                               │ 
    │                <Yes>                   <No>                   │ 
    │                                                               │ 
    └───────────────────────────────────────────────────────────────┘ 
~~~

De nuevo se deja la opción por defecto, si. Esta pregunta es sobre si se quiere dejar el antiguo directorio:
~~~
 ┌────────────────────────┤ Configuring slapd ├────────────────────────┐
 │                                                                     │ 
 │ There are still files in /var/lib/ldap which will probably break    │ 
 │ the configuration process. If you enable this option, the           │ 
 │ maintainer scripts will move the old database files out of the way  │ 
 │ before creating a new database.                                     │ 
 │                                                                     │ 
 │ Move old database?                                                  │ 
 │                                                                     │ 
 │                  <Yes>                     <No>                     │ 
 │                                                                     │ 
 └─────────────────────────────────────────────────────────────────────┘ 
~~~

Comprobación de que los cambios se han realizado correctamente:
~~~
vagrant@servidor:~$ sudo slapcat
dn: dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: dcObject
objectClass: organization
o: IES Gonzalo Nazareno
dc: paloma
structuralObjectClass: organization
entryUUID: e0668250-afca-1039-8d64-dbcecfe20547
creatorsName: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
createTimestamp: 20191210185903Z
entryCSN: 20191210185903.057531Z#000000#000#000000
modifiersName: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
modifyTimestamp: 20191210185903Z

dn: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e1NTSEF9Vk5wUDdKUmplbnQ0QXNWTmM3aU43MkxRZDNoc2ltaWk=
structuralObjectClass: organizationalRole
entryUUID: e066c030-afca-1039-8d65-dbcecfe20547
creatorsName: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
createTimestamp: 20191210185903Z
entryCSN: 20191210185903.059211Z#000000#000#000000
modifiersName: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
modifyTimestamp: 20191210185903Z
~~~

### Creación de usuarios, grupos y unidades organizativas

La información se guarda en ficheros .ldif. Estos ficheros, se recomienda, se se organicen de la siguiente forma:
- personas.ldif
- grupos.ldif
- u_organizativas.ldif

#### Personas
Creación de un fichero personas.ldif:
~~~
dn: uid=paloma,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixAccount
objectClass: inetOrgPerson
objectClass: person
cn:: UGFsb21hIGRlbCBSb2PDrW8gR2FyY8OtYSBDYW1ww7NuCg==
uid: paloma
uidNumber: 2001
gidNumber: 2000
homeDirectory: /home/paloma
loginShell: /bin/bash
userPassword: {SSHA}+qOt08A0t3aCSWR8tuksmexgOhqKwf8z
sn:: R2FyY8OtYSBDYW1ww7NuCg==
mail: palomagarciacampon08@gmail.com
givenName: paloma
~~~

> La contraseña debe aparecer cifrada. Para conocerla:
~~~
paloma@coatlicue:~/DISCO2/CICLO II/ADMINISTRACION_DE_SISTEMAS_OPERATIVOS/LDAP$ sudo slappasswd -v
[sudo] password for paloma: 
New password: 
Re-enter new password: 
{SSHA}+qOt08A0t3aCSWR8tuksmexgOhqKwf8z
~~~

> Si se quiere añadir palabras con tíldes, o carácteres especiales, se utiliza base64 de la siguiente manera:
~~~
paloma@coatlicue:~/DISCO2/CICLO II/ADMINISTRACION_DE_SISTEMAS_OPERATIVOS/LDAP$ echo Paloma del Rocío García Campón | base64
UGFsb21hIGRlbCBSb2PDrW8gR2FyY8OtYSBDYW1ww7NuCg==
~~~

#### Grupos
Creación del fichero grupos.ldif:
~~~
dn: cn=Usuarios,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: posixGroup
gidNumber: 2000
cn: Usuarios
~~~

#### Unidades Organizativas
Se crea el fichero u_organizativas.ldif:
~~~
dn: ou=People,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: top
objectClass: organizationalUnit
ou: People
~~~


### Introducción de una unidad organizativa:

Se agrega con el comando **ldapadd**, las opciones son:
- x: para usar la autentificación simple en lugar de SASL.
- D: para indicar el Distinguished Name.
- W: para que se pida la contraseña.
- f: indica el fichero que se va a utilizar.

#### Agregar unidades organizativas
~~~
ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f u_organizativas.ldif
~~~

#### Agregar grupos
~~~
ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f grupos.ldif
~~~

#### Agregar personas
~~~
ldapadd -x -D cn=admin,dc=paloma,dc=gonzalonazareno,dc=org -W -f usuario.ldif
~~~

#### Eliminar objeto
~~~
ldapdelete -x -D <Usuario con permisos para poder eliminar> <Objeto a eliminar> -W
~~~

#### Modificar objetos
~~~
ldapmodify -x -D <Usuario con permisos para poder modificar> -f <fichero con las modificaciones> -W
~~~

Para modificar se necesita un fichero que contenga las modificaciones:
~~~
dn: <identificador_del_objeto>
changetype:modify
replace: <atributo_a_modificar>
<atributo_a_modificar>: <modificación>
~~~

> Ejemplo:
~~~
dn: uid=paloma,ou=People,dc=paloma,dc=gonzalonazareno,dc=org
changetype:modify
replace: homeDirectory
homeDirectory: /home/nfs/paloma
~~~

### Consultas
~~~
ldapsearch -x -h <nombre_maquina> -b <busqueda>
~~~

Opciones más importantes:
- z 0: Para que ldap no corte la info.
- x: indica la autentificación básica.
- h: nombre de la máquina.
- b: la búsueda.

> Ejemplo: filtrar todas las uid de las personas:
~~~
ldapsearch -z 0 -x -h servidor -b ou=People,dc=paloma,dc=gonzalonazareno,dc=org | egrep "^uid: *"
~~~

~~~
vagrant@servidor:~$ ldapsearch -z 0 -x -h servidor -b ou=People,dc=paloma,dc=gonzalonazareno,dc=org | egrep "^uid: *"
uid: paloma
uid: alejandro
~~~

### ACLs

La sintaxis para crear ACLs es la siguiente:
~~~
access to <qué> [by <quién> [<acceso>] [<control>]]
~~~

Y los priviledios son:

Nivel de acceso |   Privilegios |   Descripción
|:-------------:|:-------------:|:---------------------------------------------------|
none            |0              |sin acceso
disclose        |d              |necesario para información en caso de error
auth            |dx             |necesario para autenticación (bind)
compare         |cdx            |necesario para comparar
search          |scdx           |necesario para aplicar los filtros de búsqueda
read            |rscdx          |necesario para leer los resultados de la búsqueda
add|delete      |wrscdx 	    |necesario para modifica
manage          |mwrscdx        |necesario para gestionar 

#### Ficheros de configuración de ACLs
~~~
dn: olcDatabase={<posición>}frontend,cn=config
changetype: modify
add: olcAccess
olcAccess: {<posicion>} to <qué> [by <quién> <acceso> [<control>]]



dn: olcDatabase={1}mdb,cn=config
changetype: modify
add: olcAccess
olcAccess: {3}to attrs.regex="uid=[a-zA-z0-9]*,ou=People,dc=paloma,dc=gonzalonazareno,dc=org" filter=(memberof=almacen)
    by self write