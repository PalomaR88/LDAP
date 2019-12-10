# LDAP
Las bases de datos pueden ser Relacionales (genericos) o no relaciones (específicos). Pero en paralelo se ha desarrollado los direcotrios que son un tipo de base de datos específico, simple y de información jerárquica.

Fundamentalmente lo que se guarda en los direcotrios es:
- Info de usuarios.
- Info de equipos.
- Info de grupos.
...

- También incluye un protocolo TCP/IP de acceso. 
Los directorios son muy limitados y específicos, pero todos los usuarios tiene el mismo esquema ye sto permite que sea muy portable. 

Antes había un protocolo llamado x500 (OSI) que guardaba información de todos los usuarios que están conectados a internet, este protocolo usaba protocolo DAP (Directory Access Protocol). De la misma fecha vienen los certificados x509, por eso tienen en común campos como CN, O...

Años después, cuando el protocolo x500 cayó en desuso, se llegó a la idea de que una base de datos relacionar para usuarios era innecesario. Y apareció LDAP (TCP/IP).

Usos típicos:
- Obtener acceso a equipos/servicios. Y es muy fácil gestionar permisos porque se gestionan a través de grupos de usuarios.


## Base de datos jerárquica
En LDAP el punto de partida, la raíz, se llama base. Este protocolo se utiliza a nivel coorporativo. Esta base tiene que ser compatible con toda la organización.

Para que LDAP sea compatible con el resto del mundo y no solo ser usada en la intranet, se suele usar de base el DNS de la organización (gonzalonazareno.org).

Problema: la consistencia en LDAP no está garantizada. 

- Directorios optimizados para lecturas simples

## Protocolo de acceso
Las entidades de las que se quiere guardar información se llaman objetos. Estos objetos se agrupan en otros objetos.
- Unidades organizativas (OU): para contener otro objetos dentro.
- Los objetos tiene atributos. Estos tienes características: monovaluado, obligatorios, etc. 

## Consultas
~~~
ldapsearch -x -b dc=gonzalonazareno,dc=org -h papion-ldap uid=alberto.molina
~~~
-h el servidor 
-dc nombre del ldap

## objectClass
Tipo de objetos:
- posixAccount (tipo POSIX/que es tipo UNIX pero es marca registrada, lo que se guarda en el passwd)
- person (nombre, direccion, etc)
- inetOrgPerson (mail)
- dn define al objeto por completo(uid+ou+dc, por ejemplo) ls dirección de la rama de ese objeto

## Herramientas
ldap-utils 

ldapmodrdn -> cambia el dn y de esta forma se puede mover el objeto, porque puedes modificar ou.

Interfaz gráfica: apache directory studio
web -> phpLDAPAdmin

## Instalación de un servidor LDAP
Se usará openldap: 
~~~
paloma@coatlicue:~/DISCO2/CICLO II/ADMINISTRACION_DE_SISTEMAS_OPERATIVOS/LDAP$ sudo apt install slapd
~~~

Pregunta la contraseña para el administrador, y el nombre del mismo por defecto es el nombre de la máquina:
~~~
  ┌────────────────────┤ Configuración de slapd ├─────────────────────┐
  │ Introduzca la contraseña para la entrada de administrador de su   │ 
  │ directorio LDAP.                                                  │ 
  │                                                                   │ 
  │ Contraseña del administrador:                                     │ 
  │                                                                   │ 
  │ *********________________________________________________________ │ 
  │                                                                   │ 
  │                              <Aceptar>                            │ 
  │                                                                   │ 
  └───────────────────────────────────────────────────────────────────┘ 
~~~



### Conceptos básicos
Se crea el fichero ou.ldif para las ramas principales que serán las unidades organizativas:
~~~
dn: ou=People,dc=paloma,dc=gonzalonazareno,dc=org
ou= People
objectClass: organizationalUnit

dn: ou=Groups,dc=paloma,dc=gonzalonazareno,dc=org
ou= Groups
objectClass: organizationalUnit
~~~

Para agregar el fichero:
~~~
ldapadd -x -D "cn=admin,dc=paloma,dc=coatlicue,dc=nahualt" -f ou.ldif -W
~~~
