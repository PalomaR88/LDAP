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

## Base de datos jerárquica
En LDAP el punto de partida, la raíz, se llama base. Este protocolo se utiliza a nivel coorporativo. Esta base tiene que ser compatible con toda la organización.

Para que LDAP sea compatible con el resto del mundo y no solo ser usada en la intranet, se suele usar de base el DNS de la organización (gonzalonazareno.org).

Problema: la consistencia en LDAP no está garantizada. 


## Protocolo de acceso


