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
- [audio](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#audio) 
- [businessCategory](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#businesscategory) 
- [carLicense](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#carlicense) 
- [departmentNumber](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#departmentnumber) 
- [displayName](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#displayname) 
- [employeeNumber](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#employeenumber) 
- [employeeType](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#employeenumber) 
- [givenName](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#givenname) 
- [homePhone](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#homephone) 
- [homePostalAddress](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#homepostaladdress) 
- [initials](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#initials) 
- [jpegPhoto](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#jpegphoto) 
- [labeledURI](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#labeleduri)
- [mail](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#mail) 
- [manager](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#manager) 
- [mobile](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#mobile) 
- [o](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#o) 
- [pager](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#pager) 
- [photo](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#photo) 
- [roomNumber](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#roomnumber) 
- [secretary](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#secretary) 
- [uid](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#uid) 
- [userCertificate](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#usercertificate) 
- [x500uniqueIdentifier](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#x500uniqueidentifier) 
- [preferredLanguage](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#preferredlanguage)
- [userSMIMECertificate](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#usersmimecertificate) 
- [userPKCS12](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#userpkcs12)

#### top
Clase de objeto abstracto que es el padre de cada clase de objeto LDAP. Es el que define que cada objeto en LDAP debe tener un atributo objectClass.

#### organizationalUnit
Obligatorios:
- ou 	

No obligatorios:
- [userPassword](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#userpassword) 
- searchGuide 
- seeAlso 
- businessCategory 
- x121Address 
- registeredAddress 
- destinationIndicator 
- preferredDeliveryMethod 
- telexNumber 
- teletexTerminalIdentifier 
- telephoneNumber 
- internationaliSDNNumber 
- facsimileTelephoneNumber 
- street 
- postOfficeBox 
- postalCode 
- postalAddress 
- physicalDeliveryOfficeName 
- st 
- l 
- description

# atributos
#### ou 	
Nombre de la unidad organizativa.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

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
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)
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
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

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
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### audio 
Permite almacenar audio.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)

#### businessCategory 
Categoría de negocio.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)


#### carLicense 
Valores de licencia o placa de matrícula.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### departmentNumber 
Numero de departamento.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### displayName 
Identificación por nombre.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### employeeNumber 
Número de empleado.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### employeeType 
Tipo de empleado.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### givenName 
Nombre de pila.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### homePhone 
Teléfono de casa.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### homePostalAddress 
Dirección postal.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### initials 
Iniciales.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### jpegPhoto 
Fichero jpeg (imagen).

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### labeledURI 
Etiqueta de URI.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### mail 
Correo.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### manager 
Gerente.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### mobile 
Teléfono móvil.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### o 
Organización.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### pager 
Busca.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### photo 
Foto.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### roomNumber 
Número de habitación.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### secretary 
Secretario.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)



#### userCertificate 
Certificado de usuario.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### x500uniqueIdentifier 
Método binario de identificación útil para diferenciar objetos.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### preferredLanguage 
Preferencia de idioma.

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### userSMIMECertificate 

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)


#### userPKCS12

ObjectClass:
- [inetOrgPerson](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#inetorgperson)

#### searchGuide
Guía de búsqueda.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### seeAlso 
Ver más.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)


#### x121Address 
Direcciones x.121.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### registeredAddress 
Dirección registrada.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### destinationIndicator 
Indicador de destino.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### preferredDeliveryMethod 
Preferencias en el meétodo de entrega.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### telexNumber 
Número de teletipo.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### teletexTerminalIdentifier 
Identificador de terminal teletex.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### telephoneNumber 
Número de teléfono.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### internationaliSDNNumber 
Número iSDN.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### facsimileTelephoneNumber 
Fax.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### street 
Calle.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### postOfficeBox 
Apartado de correos.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### postalCode 
Código Postal.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### postalAddress 
Dirección postal.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### physicalDeliveryOfficeName 
Nombre de la óficina de entrega física.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### st 
Provincia o estado.

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)

#### l 
Localidad. 

ObjectClass:
- [organizationalUnit](https://github.com/PalomaR88/LDAP/blob/master/glosario.md#organizationalunit)



