# LDAPs
## Creación de los certificados
Se puede ver la documentación sobre la creación de claves y certificados firmados por entidades certificadoras usando openssl en el siguiente [enlace](https://github.com/PalomaR88/HTTPS_en_el_cloud/blob/master/Practica.md#https).

Tras crear los certificados y ubicarlos en /etc/ssl/certs/paloma.gonzalonazareno.org.crt, /etc/ssl/certs/IESGonzaloNazareno.crt y /etc/ssl/private/gonzalonazareno.pem hay que cambiar las ACL con el comando **setfacl** para agregar permisos:
~~~
debian@croqueta:~$ sudo setfacl -m u:openldap:r-x /etc/ssl/openldap
debian@croqueta:~$ sudo setfacl -m u:openldap:r-x /etc/ssl/openldap/gonzalonazareno.pem
debian@croqueta:~$ sudo setfacl -m u:openldap:r-x /etc/ssl/openldap
debian@croqueta:~$ sudo setfacl -m u:openldap:r-x /etc/ssl/openldap/IESGonzaloNazareno.crt
debian@croqueta:~$ sudo setfacl -m u:openldap:r-x /etc/ssl/openldap/paloma.gonzalonazareno.org.crt
~~~

> Para el paso anterior es necesario tener instalado el paquete **acl**:
~~~
sudo apt install acl
~~~

Por último, se configura el fichero /usr/lib/ssl/openssl.cnf añadiendo la ruta correcta de dir:
~~~
[ CA_default ]

#dir            = ./demoCA              # Where everything is kept
dir             = /etc/ssl
certs           = $dir/certs            # Where the issued certs are kept
crl_dir         = $dir/crl              # Where the issued crl are kept
database        = $dir/index.txt        # database index file.
#unique_subject = no                    # Set to 'no' to allow creation of
                                        # several certs with same subject.
new_certs_dir   = $dir/newcerts         # default place for new certs.

certificate     = $dir/certs    # The CA certificate
serial          = $dir/serial           # The current serial number
crlnumber       = $dir/crlnumber        # the current crl number
                                        # must be commented out to leave $
crl             = $dir/crl.pem          # The current CRL
private_key     = $dir/private  # The private key
~~~

## Instalación de LDAP
Se puede ver la documentación sobre la instalación y la configuración de LDAP en el siguiente [enlace](https://github.com/PalomaR88/LDAP/blob/master/Primeros_pasos_LDAP.md#primeros-pasos-en-ldap).

## Configuración de LDAPs
Para la configuración de LDAPs se crea un fichero .ldif con el que se modificará cn=config, en nuestro caso será ldaps.ldif de la siguiente forma:
~~~
dn: cn=config
changetype: modify
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/openldap/IESGonzaloNazareno.crt
-
replace: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/openldap/paloma.gonzalonazareno.org.crt
-
replace: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/openldap/gonzalonazareno.pem
~~~

Y se añaden los cambios que se han configurado en ldaps.ldif:
~~~
debian@croqueta:~$ sudo ldapmodify -Y EXTERNAL -H ldapi:/// -f ldaps.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "cn=config"
~~~

> Comprobación de la modificación:
~~~
debian@croqueta:~$ sudo slapcat -b "cn=config" | grep -E "olcTLS"
olcTLSCACertificateFile: /etc/ssl/certs/IESGonzaloNazareno.crt
olcTLSCertificateFile: /etc/ssl/certs/paloma.gonzalonazareno.org.crt
olcTLSCertificateKeyFile: /etc/ssl/private/gonzalonazareno.pem
~~~

> Comprobación de la validez de la nueva configuración de LDAP:
~~~
debian@croqueta:~$ sudo slaptest -u
config file testing succeeded
~~~

Hay que configurar el fichero /etc/ldap/ldap.conf para indicar el certificado de la entidad certificadora:
~~~
TLS_CACERT      /etc/ssl/certs/IESGonzaloNazareno.crt
~~~

Y se restaura el servicio de slapd:
~~~
debian@croqueta:/etc/ldap$ sudo systemctl restart slapd
~~~

Comprobación:
~~~
debian@croqueta:~$ sudo ldapsearch -x -H ldap://croqueta.paloma.gonzalonazareno.org:636 -b "cn=admin,dc=paloma,dc=gonzalonazareno,dc=org"
ldap_result: Can't contact LDAP server (-1)
debian@croqueta:~$ sudo ldapsearch -x -H ldaps://croqueta.paloma.gonzalonazareno.org:636 -b "cn=admin,dc=paloma,dc=gonzalonazareno,dc=org"
# extended LDIF
#
# LDAPv3
# base <cn=admin,dc=paloma,dc=gonzalonazareno,dc=org> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# admin, paloma.gonzalonazareno.org
dn: cn=admin,dc=paloma,dc=gonzalonazareno,dc=org
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
~~~
