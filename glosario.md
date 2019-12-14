# objectClass
#### posixAccount: 	
Obligatorios:
- [cn](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#cn) 
- [uid](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#uid) 
- [uidNumber](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#uidnumber) 
- [gidNumber](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#gidnumber)
- [homeDirectory](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#homedirectory)

No obligatorios:
- [userPassword](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#userpassword) 
- [loginShell](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#loginshell)
- [gecos](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#gecos)
- [description](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#description) 	

Esquema: nis.schema

#### inetOrgPerson:
No obligatorios:
- audio 
- businessCategory 
- carLicense 
- departmentNumber 
- displayName 
- employeeNumber 
- employeeType 
- givenName 
- homePhone 
- homePostalAddress 
- initials 
- jpegPhoto 
- labeledURI 
- mail 
- manager 
- mobile 
- o 
- pager 
- photo 
- roomNumber 
- secretary 
- uid 
- userCertificate 
- x500uniqueIdentifier 
- preferredLanguage 
- userSMIMECertificate 
- userPKCS12


# atributos
#### cn
CommonName

ObjectClass:
- person
- organizationalPerson
- organizationalRole
- groupOfNames
- applicationProcess
- applicationEntity
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)
- device

#### uid 
Nombre de usuario/valor único.

ObjectClass:
- account
- inetOrgPerson
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### uidNumber 
Número del usuario.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### gidNumber 
Número del grupo al que el usuario pertenece.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

####  homeDirectory
Ruta del home del usuario.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### userPassword 
Contraseña del usuario.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### loginShell 
Shell del usuario.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### gecos 
Se creó en POSIX se creó para contener los atributos no Unix requeridos.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### description 
Descripción.

ObjectClass:
- [posixAccount](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#posixaccount)

#### audio 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)

#### businessCategory 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### carLicense 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### departmentNumber 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### displayName 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### employeeNumber 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### employeeType 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### givenName 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### homePhone 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### homePostalAddress 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### initials 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### jpegPhoto 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### labeledURI 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### mail 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### manager 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### mobile 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### o 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### pager 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### photo 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### roomNumber 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### secretary 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### uid 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### userCertificate 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### x500uniqueIdentifier 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### preferredLanguage 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### userSMIMECertificate 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### userPKCS12

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)
