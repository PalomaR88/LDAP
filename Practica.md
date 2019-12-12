# Usuarios, grupos y ACLs en LDAP

### Creación de usuarios
Se van a crear 10 usuarios con nombres en LDAP. Serán objetos de tipo posixAccount e inetOrgPerson con un atributo userPassword.

Se buscan los atributos que contienen las clases posixAccount e inetOrgPerson. Se va a usar la página [zytrax](https://www.zytrax.com/books/ldap/ape/).
------> cambiar esto para crear un glosario
Atributos de posixAccount: 	
- Obligatorios:
##### cn 
##### uid 
##### uidNumber 
##### gidNumber 
##### homeDirectory
- No obligatorios:
##### userPassword 
##### loginShell 
##### gecos 
##### description 	
- Esquema: nis.schema

Atributos de 



### Crea 3 grupos en LDAP dentro de una unidad organizativa diferente que sean objetos del tipo groupOfNames. Estos grupos serán: comercial, almacen y admin

### Añade usuarios que pertenezcan a:
- Solo al grupo comercial
- Solo al grupo almacen
- Al grupo comercial y almacen
- Al grupo admin y comercial
- Solo al grupo admin

### Modifica OpenLDAP apropiadamente para que se pueda obtener los grupos a los que pertenece cada usuario a través del atributo "memberOf"

### Crea las ACLs necesarias para que los usuarios del grupo almacen puedan ver todos los atributos de todos los usuarios pero solo puedan modificar las suyas

### Crea las ACLs necesarias para que los usuarios del grupo admin puedan ver y modificar cualquier atributo de cualquier objeto


# LDAPs
### Configura el servidor LDAP de croqueta para que utilice el protocolo ldaps:// a la vez que el ldap:// utilizando el certificado x509 de la práctica de https o solicitando el correspondiente a través de gestiona.

### Realiza las modificaciones adecuadas en el cliente ldap de croqueta para que todas las consultas se realicen por defecto utilizando ldaps://

