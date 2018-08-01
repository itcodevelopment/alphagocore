# Crear un Usuario
Se debera enviar una peticion de tipo **POST** a la siguiente ruta: **/api/users/**

### Datos Requeridos:

|Clave | Valor|
|--|--|
| **Name** |Nombre de  la persona (*String*)  |
|**Lastname**| Apellido de la persona (*String*)|
|**Email**| Email de la persona (*String*)|
|**Phone**| Telefono de contacto (*String*)|
|**Username**|Usuario para autenticar (*String*)|
|**Company_name**|Nombre de la compania (*String*)|

### Estructura del JSON:
```json
{
	"Name" : "Pedro",
	"Lastname": "Castillo",
	"Email": "pedro@itcoint.com",
	"Phone": "89586444",
	"Username": "pedro",
	"Password": "Intlog6151$%",
	"Company_name": "ITCO"
}
```
# Login Usuario
Se debera enviar una peticion de tipo **POST** a la siguiente ruta:  **/api/users/login**

### Datos Requeridos:

|Clave|  Valor|
|--|--|
| **username** | Nombre de usuario (*String*) |
|**password**|Contrasena de usuario (*String*)|

### Estructura del JSON
```json
{
	"username": "pedro",
	"password": "Intlog6151$%"
}
```
### Respuesta del recurso:

Esto respondera un SessionKey que sera requerido para algunas peticiones ( Esto se debera guardar en el Local Storage para persistirlo )

El session key tiene una validez de **1 hora** por lo cual despues de este periodo debera solicitarse otro.
```json
{
    "sessionKey": "d1dnMG5RdnQ0YXFwMjczQ3pvdXM4UT09OjoSsfF4d0+BkExpS5YCO32C"
}
```
# Generar API Key
Este API Key que es generado por motivos de seguridad para el uso del API de **Alpha Go Core** y es totalmente diferente al **SessionKey** generado por **CRL**

Se debera enviar una peticion de tipo **POST** a la siguiente ruta: **/api/create/token**

### Datos Requeridos:
|Clave|Valor  |
|--|--|
| **Email** | Email del usuario registrado (*String*) |
|**Password**|Password del usuario registrado (*String*)|

### Estructura del JSON:
```json
{
	"Email": "pedro@itcoint.com",
	"Password": "Intlog6151$%"
}
```
### Respuesta del recurso:
```json
{
    "apiKey": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk1OTEyMzd9.Pz6pdumUn6_0jthhB0EW0aLt2DPXS1Zi2d6otsx6P6U"
}
```
# Crear una compania
Se debera enviar una peticion de tipo **POST** a la siguiente ruta: **/api/company**
### Datos Requeridos:

|Clave| Valor  |
|--|--|
| **Name** | Nombre de la compania (*String*)|
| **CeUser** |Usuario de Comprobantes Electronicos (*String*)| 
|**CePassword**|Contrasena de Comprobantes Electronicos (*String*)|
|**CePin**|Pin de Comprobantes Electronicos (*String*)|
|**Environment**|Entorno en que se carga el certificado **Stag** - **Prod** (*String*) |
|**UserName**|Usuario Logueado (*String*)|
|**SessionKey**|Session Key del usuario logueado (*String*)|
|**CrlCertificateCode**| Se debe enviar vacio (*String*)|
|**FilePath**|Se debe enviar vacio (*String*)|
|**Cert**|Certificado .p12 codificado en **base64** (*Base 64 String*)|

[Como Crear Un Usuario](#crear-un-usuario)
[Obtener Session Key](#login-usuario)

### Estructura del Json:
Todos los campos son requeridos sin excepcion.
```json
{
	"Name" : "ITCO",
	"CeUser" : "prueba",
	"CePassword" : "123",
	"CePin" : "1234",
	"UserName": "pedro",
	"SessionKey" : "eTIzb3FiZVUrd3g1N0M2TGo0UlFOQT09OjpjNb1uk2xAobi27LntChi8",
	"Environmet": "stag",
	"CrlCertificateCode": "",
	"FilePath": "",
	"Cert": "(CERTIFICADO EN BASE64)"
}
```
### Respuesta del recurso:
```json
{
    "data": {
        "id": 4,
        "Name": "ITCO",
        "CeUser": "prueba",
        "CePassword": "123",
        "CePin": "1234",
        "CrlCertificateCode": "c73b93a548371afcdd5b054aa98ec0ba",
        "updatedAt": "2018-06-21T17:17:10.557Z",
        "createdAt": "2018-06-21T17:17:10.557Z"
    },
    "status": 201
}
```
## Obtener todas las companias:
Para obtener todas las companias, debera enviar una peticion de tipo **GET** a la siguiente ruta: **/api/companies**
### Datos requeridos:
| Clave | Valor |
|--|--|
| **Authorization** |Corresponde al API Key de AGC (*String*) |

### Respuesta del recurso:
```json
[
    {
        "id": 1,
        "Name": "ITCO",
        "CeUser": "prueba",
        "CePassword": "123",
        "CePin": "1234",
        "Environmet": "stag",
        "CrlCertificateCode": "7e4f44938a966bbb669aecc0331694bd",
        "FilePath": "./certs/cert1529615544862.p12",
        "createdAt": "2018-06-21T21:12:25.300Z",
        "updatedAt": "2018-06-21T21:12:25.300Z"
    },
    {
        "id": 2,
        "Name": "TS",
        "CeUser": "prueba",
        "CePassword": "123",
        "CePin": "1234",
        "Environmet": "stag",
        "CrlCertificateCode": "70348e40ed539e03caf0f0c00a3732ab",
        "FilePath": "./certs/cert1529615561259.p12",
        "createdAt": "2018-06-21T21:12:41.696Z",
        "updatedAt": "2018-06-21T21:12:41.696Z"
    }
]
```
## Obtener Una Compania

Para obtener todas las companias, debera enviar una peticion de tipo **GET** a la siguiente ruta: **/api/company/:id** 
### Datos requeridos:
| Clave | Valor |
|--|--|
| **Authorization** |Corresponde al API Key de AGC (*String*) |
|**id**|Id de la compania que se quiere obtener (*Int*)|

### URL de ejemplo:
/api/company/1

### Respuesta del recurso:
```json
{
    "id": 1,
    "Name": "ITCO",
    "CeUser": "prueba",
    "CePassword": "123",
    "CePin": "1234",
    "Environmet": "stag",
    "CrlCertificateCode": "7e4f44938a966bbb669aecc0331694bd",
    "FilePath": "./certs/cert1529615544862.p12",
    "createdAt": "2018-06-21T21:12:25.300Z",
    "updatedAt": "2018-06-21T21:12:25.300Z"
}
```

## Asignar un usuario a una compañía
Un usuario puede pertenecer a una o más compañías, por lo tanto para asignar a un usuario a una compañía se deberá realizar por medio de un **POST** a la siguiente ruta: **/api/company/user**

```json
{
	"userId": 1,
	"companyId": 6
}
```

### Respuesta del recurso:

```json
[
    {
        "id": 1,
        "Name": "Pedro",
        "Lastname": "Castillo",
        "Email": "pedro@itcoint.com",
        "Phone": "89586444",
        "Username": "pedro",
        "Password": "Intlog6151$%",
        "Company_name": "ITCO",
        "ApiToken": null,
        "CrlSessionToken": "QU03NWd3ZXJMbHFGS1JxODJESDdFQT09Ojo14U7qQYGk+53I3xb57Qw6",
        "createdAt": "2018-06-29T17:09:18.956Z",
        "updatedAt": "2018-07-02T15:28:02.814Z",
        "Companies": [
            {
                "id": 2,
                "Name": "TS",
                "CeUser": "prueba",
                "CePassword": "123",
                "CePin": "1234",
                "Environmet": "stag",
                "CrlCertificateCode": "630360f1270cb832a395f0f16dd2c174",
                "FilePath": "./certs/cert1530292769727.p12",
                "CompanyAPI": "ff191b1d-f2c8-4140-9402-33d3f0bf4c8e",
                "createdAt": "2018-06-29T17:19:30.217Z",
                "updatedAt": "2018-06-29T17:19:30.217Z",
                "UserCompanies": {
                    "createdAt": "2018-07-02T16:00:57.145Z",
                    "updatedAt": "2018-07-02T16:00:57.145Z",
                    "CompanyId": 2,
                    "UserId": 1
                }
            }
        ]
    }
]
```

Este mismo devolverá la información del usuario con las compañías a las que pertenece.

# Token Hacienda
Para generar un token de acceso para hacienda es necesario enviar una solicitud de tipo **POST** a la siguiente ruta: **/api/create/access-token**

### Datos Requeridos:
|Clave| Valor |
|--|--|
| **authorization** | Esto se envia en el header de la peticion y correspode al APIKEY del usuario Alpha Go Core (*String*) |
|**Environment**|**api-stag** - **api-prod** (*String*)|
|**CeUser**|Usuario de comprobantes electronicos|
|**CePassword**|Contrasena de comprobantes electronicos|

### Estructura del JSON

Ejemplo enviado desde NodeJS con Request:
```js
headers: 
   {
      Content-Type: 'application/json',
      Authorization: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk2MDk2NjB9.9aq0zRpxlKf9NPF7rpZpQ0nKMQ1Zu0mqGDd9_VKpB9I' 
     },
  body: 
   { 
     Environment: 'api-stag',
     CeUser: 'cpj-3-101-660919@stag.comprobanteselectronicos.go.cr',
     CePassword: 'E{ToB(ebW&F?%%!}r!G]' }
  };
```
[Generar autorizacion (API KEY)](#generar-api-key)

### Respuesta del recurso:
```json
{
    "code": 201,
    "accessToken": "eyJhbGciOiJSUzI1NiJ9.eyJqdGkiOiIzNjY0NzAyMS1lYTRkLTQxYjItOTRkNi1hMTMyYzZjMzA0NGIiLCJleHAiOjE1Mjk2MTA3NDUsIm5iZiI6MCwiaWF0IjoxNTI5NjEwNDQ1LCJpc3MiOiJodHRwczovL2lkcC5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IvYXV0aC9yZWFsbXMvcnV0LXN0YWciLCJhdWQiOiJhcGktc3RhZyIsInN1YiI6IjA4YWY1MzI0LTdkYWYtNDhhMC05NTQwLTFjOGRmNzVjNGU4NCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFwaS1zdGFnIiwic2Vzc2lvbl9zdGF0ZSI6ImI3ZmIwOWJhLTNmZWMtNGQxNC05MDYwLWE2M2NkOWFhOWNkMCIsImNsaWVudF9zZXNzaW9uIjoiNDY1ZDZmNzktNTNhOC00YjY0LTllMTktZjhiZTJiNzZiODUzIiwiYWxsb3dlZC1vcmlnaW5zIjpbXSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LXByb2ZpbGUiXX19LCJuYW1lIjoiQUxGQVJPICYgSEVSTkFOREVaIElUIENPUlBPUkFUSU9OIElUQ08gU09DSUVEQUQgQU5PTklNQSAiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJjcGotMy0xMDEtNjYwOTE5QHN0YWcuY29tcHJvYmFudGVzZWxlY3Ryb25pY29zLmdvLmNyIiwiZ2l2ZW5fbmFtZSI6IkFMRkFSTyAmIEhFUk5BTkRFWiBJVCBDT1JQT1JBVElPTiBJVENPIFNPQ0lFREFEIEFOT05JTUEiLCJwb2xpY3ktaWQiOiI1OGE2MjAzMzc2ZWFlMTQwOGNlNWU3ZGQiLCJlbWFpbCI6ImNwai0zLTEwMS02NjA5MTlAc3RhZy5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IifQ.eyGqDfqb4aHw_cA8x2dQCGdaH0Z-qOBFEwHJ15pS2MWqcCti2aw3gC_2riZS9Ss-gI1Q4eTNWpbelo_sRf6-DEvx4P6Q-deDWwgFEzZuQj2srUi6tN36sT25XXtsz-Y2baCmn13cWnfWkrFqKx6Gs4nTw9fXcco21QLpkj4YW8j7l3eFuFHzRj20JR9wqb8ZpNmH2Y9KjYPr9eL2pPPWVMDqt4NeVSARMkbH0I9hD8-s7GIZyUnjpXBQh8kkQ679kNwDpPvbC9h7SRRgKqA6Mn7ZQ0Lvu8XLveyNR4ptOSfYnWn4sgCFwO5oPH1rN6nqT_FkSq7InvoKE0mLZEdTfA",
    "expires": 300
}
```
# Obtener Token de hacienda por medio de una funcion asincrona
Se puede obtener un token de hacienda por medio de la llamada de una funcion asincrona.
```js 
const  generic  =  require("./controllers/generic-functions");

let  datos  = {
	Environment:  'api-stag',
	CeUser:  'cpj-3-101-660919@stag.comprobanteselectronicos.go.cr',
	CePassword:  'E{ToB(ebW&F?%%!}r!G]'
}

generic.getTaxationToken(datos).then((data)=>{
	console.log(data);
})
```

### Respuesta de la funcion en data:

```json
{ code: 201,
  accessToken: 'eyJhbGciOiJSUzI1NiJ9.eyJqdGkiOiJkNTdhODMxMS1iZTc0LTQ3YmQtYjczMi1lNWNkNGVlOGU3MjgiLCJleHAiOjE1Mjk5NjE5MTksIm5iZiI6MCwiaWF0IjoxNTI5OTYxNjE5LCJpc3MiOiJodHRwczovL2lkcC5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IvYXV0aC9yZWFsbXMvcnV0LXN0YWciLCJhdWQiOiJhcGktc3RhZyIsInN1YiI6IjA4YWY1MzI0LTdkYWYtNDhhMC05NTQwLTFjOGRmNzVjNGU4NCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFwaS1zdGFnIiwic2Vzc2lvbl9zdGF0ZSI6ImU2Mzg5ZDQ0LTk1N2EtNDUxYi1hNTdmLWY2ZmNlZmY3MWZjOCIsImNsaWVudF9zZXNzaW9uIjoiZjJjMjVhMGYtYWMyZi00YzFhLWIwMWUtZGU3ZGYyMDU0OTUxIiwiYWxsb3dlZC1vcmlnaW5zIjpbXSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LXByb2ZpbGUiXX19LCJuYW1lIjoiQUxGQVJPICYgSEVSTkFOREVaIElUIENPUlBPUkFUSU9OIElUQ08gU09DSUVEQUQgQU5PTklNQSAiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJjcGotMy0xMDEtNjYwOTE5QHN0YWcuY29tcHJvYmFudGVzZWxlY3Ryb25pY29zLmdvLmNyIiwiZ2l2ZW5fbmFtZSI6IkFMRkFSTyAmIEhFUk5BTkRFWiBJVCBDT1JQT1JBVElPTiBJVENPIFNPQ0lFREFEIEFOT05JTUEiLCJwb2xpY3ktaWQiOiI1OGE2MjAzMzc2ZWFlMTQwOGNlNWU3ZGQiLCJlbWFpbCI6ImNwai0zLTEwMS02NjA5MTlAc3RhZy5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IifQ.Z2e-iUyojjM0CVbhNCMqLoE9XfunGO6l-vP7FktRR0ucZQA5U_UkJGqk54sBym2Qmbg8S1cXLKzEb7p6MJRW5EiXgkvtpWxv4QcTZDNcPAcLxYhoE9iOHRNI_crBhHcGKf_Jbl1sAxbY3NA1BKVCMoBmkIDFo7KqrJ36qyWT8JD2V7f9Y2PVo6A79ZsWi-ly0F3ebGZ2gC72S09xq2ES4J7DrOifr_-oDrP9TDGY0i-rIAF7mUby4ri-90gUAAe8Mt0DgBiu2m6aFh3WePDgHKdoQODcHOWXFZO01EpokkukgUjXzqv8D0kz3unfI7cIa8SfNeDlOYUKqQr8QuyRCA',
  expires: 300 }
```

La sección del *accessToken* es lo importante, ya que eso es lo que enviaremos a hacienda con el resto de infomacion para el envio de los comprobantes y consultas.

El token expira en 300s

# Clave para firmar documentos
Para generar una clave que previamente puede ser utilizada para firmar los diferentes tipos de documentos xml se debe enviar una peticion de tipo **POST** a la siguiente ruta : **/api/generate/document-key**

### Datos requeridos: 
|  Clave|  Valor|
|--|--|
|**TipoDocumento**|  FE - ND - NC - TE - CCE - CPCE - RCE (*String*)|
|**TipoCedula**| fisico - juridico (*String*)|
|**Cedula**|Numero de cedula sin guiones (*String*)|
|**Situacion**|normal - contingencia - sininternet (*String*)|
|**Consecutivo**|Consecutivo de factura sin letras (Solo digitos) (*String*)|
|**Codigo de Seguridad** | codigo de 8 numeros (*String*)|
|**Terminal**| Numero de terminal (*String*)|
|**Sucursal**|Numero de sucursal (*String*)|
|**SessionKey**|SessionKey del usuario logueado (*String*)|
|**User**| Nombre de usuario logueado|

Nota: **Terminal** y **Sucursal**  son campos opcionales y pueden no ser enviados. 

### Estrucuctura del JSON:
```json
{
	"TipoCedula": "fisico",
	"Cedula": "118470589",
	"Situacion": "normal",
	"CodigoPais": "506",
	"Consecutivo": "01",
	"CodigoSeguridad": "01010101",
	"TipoDocumento": "FE",
	"SessionKey": "SHhnbGtVSEJlV3BCUlhFcFI4RE4xdz09OjpquPlO+d01kO61acnZrtBE",
	"User": "pedro"
}
```
### Respuesta del recurso:
```json
{
    "code": 200,
    "msg": "ok",
    "data": {
        "clave": "50625061800011847058900100001010000000001101010101",
        "consecutivo": "00100001010000000001"
    }
}
```

# Crear clave por medio de una funcion
Si la clave no se desea obtener por medio del endpoint, se puede obtener mediante el codigo de la siguiente manera:
```js
const generic = require("./controllers/generic-functions");

let datos = {
    "TipoCedula": "fisico",
    "Cedula": "118470589",
    "Situacion": "normal",
    "CodigoPais": "506",
    "Consecutivo": "10203040",
    "CodigoSeguridad": "01010101",
    "TipoDocumento": "RCE",
    "SessionKey": "RlpaekZBZnluV0wrZkpLYkVkQVFxZz09OjqYXJ8pAjr0MSx33bgs2Pcf",
    "User": "pedro"
}

generic.documentKey(datos).then((data) => {
    console.log(data);
})
```
### Retorna el siguiente valor en data:
```json
{ code: 200,
  msg: 'ok',
  data:
	 { 
	     clave: '50625061800011847058900100001070010203040101010101',
         consecutivo: '00100001070010203040'
     } 
}
```

# Crear Documento
Se debe de enviar una petición de tipo **POST** a la siguiente ruta: **/api/invoice** para todos los casos (FE, NC, TE, ND)

## Datos requeridos
- **CompanyAPI:** Id de la compañía creada 
- **Environment:** Ambiente en el que se envía la factura
- **Key**
	- **Branch:** Numero de la sucursal donde se crea el documento
		>  Máximo 3 dígitos. 
		**Requerido**
	
	- **Terminal:** Numero de la terminal donde se crea el documento
		>  Máximo 5 dígitos. 
		**Requerido**
	
	- **Type:** Tipo de documento
		>  Ver Anexo de Tablas. Tabla #01. 
		**Requerido**
	
	- **Voucher:** Numero consecutivo del comprobante
		>  Máximo 10 dígitos. 
		**Requerido**
	
	- **Country:** Código de país
		>  3 dígitos. 
		**Requerido**

	- **Situation:** Situación de presentación del documento
		>  Ver Anexo de Tablas. Tabla #01. 
		**Requerido**
		
- **Header**
	- **Date:** Fecha de creación del documento
		>  YYYY-MM-DDThh:mi:ss[Z|(+|-)hh:mm]. Ejemplo: 2016-09-26T13:00:00+06:00. 
		**Requerido**
	
	- **TermOfSale:** Condición de venta
		>  Ver Anexo de Tablas. Tabla #02. 
		**Requerido**
		
	- **CreditTerm:** Plazo del crédito. 
		>  En caso de contado “0”. 
		**Requerido**
		
	- **PaymentMethod:** Medio de pago de la factura
		>  **Requerido para Factura Electrónica y Tiquete Electrónico.**

- **Receiver (Puede ser omitido en caso de que sea un Tiquete Electrónico)**
	- **Name:** Nombre o razón social del receptor
		>  Máximo 80 caracteres. 
		**Requerido**
	
	- **Identification**
		- **Type:** Tipo de identificación del receptor
			>  Ver Anexo de Tablas. Tabla #03. 
			Máximo 2 dígitos. 
			**Requerido**
	
		- **Number:** Número de cédula física/jurídica/NITE/DIMEX del receptor
			>  Ver Anexo de Tablas. Tabla #03. 
			Máximo 12 dígitos. 
			**Requerido**
			
	- **Email:** Correo electrónico del receptor
		>  \s*\w+([-+.']\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*\s*. 
		**Requerido**
	
- **Detail**
	- **0** 
		> Máximo 1000 líneas por documento.
	
		- **Number:** Numero de línea
			>  **Requerido**
	
		- **Code**
			- **Type:** Tipo de Código de producto/servicio
				>  Número decimal compuesto por 13 enteros y 3 decimales 
				Máximo 2 digitos
				Ver Anexo de Tablas. Tabla #04
				**Requerido**
				
			- **Code:** Código
				>  Máximo 20 caracteres
				**Requerido**
				
		- **Quantity:** Cantidad
			>  Número decimal compuesto por 13 enteros y 3 decimales 
			**Requerido**
	
		- **UnitOfMeasure:** Código de la unidad de medida
			>  **Requerido**
	
		- **CommercialUnitOfMeasure:** Nombre comercial de la unidad de medida
			>  Máximo 20 caracteres
	
		- **Detail:** Detalle de la mercancía transferida o servicio prestado
			>  Máximo 160 caracteres
			**Requerido**
	
		- **UnitPrice:** Precio Unitario
			>  Número decimal compuesto por 13 enteros y 3 decimales 
			**Requerido**
	
		- **TotalAmount:** Monto total de la multiplicación de la cantidad por el precio unitario
			>  Número decimal compuesto por 13 enteros y 3 decimales 
			**Requerido**
	
		- **Discount:** Monto de descuentos concedidos
			>  Número decimal compuesto por 13 enteros y 3 decimales 
	
		- **NatureOfDiscount:** Descripción del descuento concedido
			>  Máximo 80 caracteres
			**Requerido si aplica descuento**
	
		- **SubTotal:** Se obtiene de la resta del campo “monto total” menos “monto de descuento concedido"
			>  Número decimal compuesto por 13 enteros y 3 decimales 
			**Requerido**
	
		- **Tax**
			- **0**
				- **Code:** Código del impuesto
					>  Ver Anexo de Tablas. Tabla #05
					2 dígitos
					**Requerido**
	
				- **Rate:** Porcentaje del impuesto
					>  Número decimal compuesto por 4 enteros y 2 decimales
					**Requerido**
	
				- **Amount:** Monto del impuesto. Se obtiene de la multiplicación del campo subtotal por la tarifa
					>  Número decimal compuesto por 13 enteros y 5 decimales
					**Requerido**
				
				- **Exoneration**
					- **DocumentType:** Tipo de documento de exoneración o de autorización
						>  Ver Anexo de Tablas. Tabla #06
						**Requerido**
					- **DocumentNumber:** Número de documento de exoneración o de autorización
						>  Máximo 17 caracteres
						**Requerido**
					- **InstitutionName:** Nombre de la institución a la que estamos exonerando
						>  Máximo 80 caracteres
						**Requerido**
					- **IssueDate:** Fecha de emisión del documento de exoneración o de autorización
						>  YYYY-MM-DDThh:mi:ss[Z|(+|-)hh:mm]. Ejemplo: 2016-09-26T13:00:00+06:00. 
						**Requerido**
					- **TaxAmount:** Monto del impuesto Exonerado o autorizado sin impuesto
						>  Número decimal compuesto por 13 enteros y 5 decimales.
						**Requerido**
					- **PurchasePercentage:** Porcentaje de la compra autorizada o exoneración
						>  Máximo 3 dígitos
						**Requerido**
	
		- **TotalLineAmount:** Total por línea de detalle. Se obtiene de la suma de los campos “subtotal” mas “monto del impuesto”
			>  Número decimal compuesto por 13 enteros y 3 decimales 
			**Requerido**
	
- **Summary**
	- **Currency:** Código de la moneda
		>  3 caracteres
		**Requerido**
	
	- **ExchangeRate:** Tipo de cambio
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalTaxedService:** Total servicios gravados con IV
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalExemptService:** Total servicios exentos de IV
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalTaxedGoods:** Total mercadería gravada con IV
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalExemptGoods:** Total mercadería exenta de IV
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalTaxed:** Total gravado
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalExempt:** Total exento
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalSale:** Total de venta
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalDiscounts:** Total descuentos
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalNetSale:** Total de venta neta
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalTaxes:** Total de impuestos
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**
	
	- **TotalVoucher:** Total de comprobante
		>  Número decimal compuesto por 13 enteros y 3 decimales 
		**Requerido**

- **Reference**
	- **0** 
		> Máximo 10 referencias.
		- **DocumentType:** Tipo de documento de referencia
			>  Ver Anexo de Tablas. Tabla #01
			**Requerido**
		- **DocumentNumber:** Clave numérica del comprobante 	electrónico o consecutivo del documento de referencia
			>  50 dígitos
			**Requerido**
		- **DateOfIssue:** Fecha de emisión del documento de 	referencia
			>  **Requerido**
		- **Code:** Código de referencia
			>  Ver Anexo de Tablas. Tabla #07
			**Requerido**
		- **Reason:** Razón de la referencia
			>  Máximo 180 caracteres.
			**Requerido**

	## Ejemplo del JSON para Factura Electrónica, Tiquete Electrónico y Nota de Crédito** (Con impuesto)
```json
{
	"CompanyAPI": "78dd8617-c4f0-453b-bd5e-1912f124e731",
	"Environment": "stag",
	"Key": {
		"Branch": "01",
		"Terminal": "1",
		"Type": "01",
		"Voucher": "505",
		"Country": "506",
		"Situation": "1"
	},
	"Header": {
		"Date": "2018-06-20T16:15:21-06:00",
		"TermOfSale": "02",
		"CreditTerm": "15",
		"PaymentMethod": "03"
	},
	"Receiver": {
		"Name": "Los patitos S.A",
		"Identification": {
			"Type": "02",
			"Number": "3101234567"
		},
		"Email": "info@lospatitos.com"
	},
	"Detail": [{
		"Number": "1",
		"Code": {
			"Type": "04",
			"Code": "CONTRL."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Control de acceso Hikvision Voltaje DC 00V/1a",
		"UnitPrice": 213.0,
		"TotalAmount": 213.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 213.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 27.69,
			"Exoneration": null
		}],
		"TotalLineAmount": 240.69
	}, {
		"Number": "2",
		"Code": {
			"Type": "04",
			"Code": "ENRVPN."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys",
		"UnitPrice": 265.0,
		"TotalAmount": 265.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 265.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 34.45,
			"Exoneration": {
				"DocumentType": "01",
				"DocumentNumber": "100",
				"InstitutionName": "Ministerio de Hacienda",
				"IssueDate": "2016-09-26T13:00:00+06:00",
				"TaxAmount": 130,
				"PurchasePercentage": 10
			}
		}],
		"TotalLineAmount": 299.45
	}],
	"Summary": {
		"Currency": "USD",
		"ExchangeRate": 570.31,
		"TotalTaxedService": 478.0,
		"TotalExemptService": 0.0,
		"TotalTaxedGoods": 0.0,
		"TotalExemptGoods": 0.0,
		"TotalTaxed": 478.0,
		"TotalExempt": 0.0,
		"TotalSale": 478.0,
		"TotalDiscounts": 0.0,
		"TotalNetSale": 478.0,
		"TotalTaxes": 62.14,
		"TotalVoucher": 540.14
	},
	"Reference": [{
		"DocumentType": "01",
    	"DocumentNumber": "50631071800310166091900100001010000000108152884101",
    	"DateOfIssue": "2018-06-13T16:02:28-06:00",
    	"Code": "01",
    	"Reason": "Error en la informacion del cliente"
	}],
	"Other": null
}
```
## Ejemplo del JSON para Factura Electrónica, Tiquete Electrónico y Nota de crédito** (Sin impuesto)
```json
{
	"CompanyAPI": "78dd8617-c4f0-453b-bd5e-1912f124e731",
	"Environment": "stag",
	"Key": {
		"Branch": "01",
		"Terminal": "1",
		"Type": "01",
		"Voucher": "505",
		"Country": "506",
		"Situation": "1"
	},
	"Header": {
		"Date": "2018-06-20T16:15:21-06:00",
		"TermOfSale": "02",
		"CreditTerm": "15",
		"PaymentMethod": "03"
	},
	"Receiver": {
		"Name": "Los patitos S.A",
		"Identification": {
			"Type": "02",
			"Number": "3101234567"
		},
		"Email": "info@lospatitos.com"
	},
	"Detail": [{
		"Number": "1",
		"Code": {
			"Type": "04",
			"Code": "CONTRL."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Control de acceso Hikvision Voltaje DC 00V/1a",
		"UnitPrice": 213.0,
		"TotalAmount": 213.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 213.0,
		"Tax": null,
		"TotalLineAmount": 240.69
	}, {
		"Number": "2",
		"Code": {
			"Type": "04",
			"Code": "ENRVPN."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys",
		"UnitPrice": 265.0,
		"TotalAmount": 265.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 265.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 34.45,
			"Exoneration": {
				"DocumentType": "01",
				"DocumentNumber": "100",
				"InstitutionName": "Ministerio de Hacienda",
				"IssueDate": "2016-09-26T13:00:00+06:00",
				"TaxAmount": 130,
				"PurchasePercentage": 10
			}
		}],
		"TotalLineAmount": 299.45
	}],
	"Summary": {
		"Currency": "USD",
		"ExchangeRate": 570.31,
		"TotalTaxedService": 478.0,
		"TotalExemptService": 0.0,
		"TotalTaxedGoods": 0.0,
		"TotalExemptGoods": 0.0,
		"TotalTaxed": 478.0,
		"TotalExempt": 0.0,
		"TotalSale": 478.0,
		"TotalDiscounts": 0.0,
		"TotalNetSale": 478.0,
		"TotalTaxes": 62.14,
		"TotalVoucher": 540.14
	},
	"Reference": [{
		"DocumentType": "01",
    	"DocumentNumber": "50631071800310166091900100001010000000108152884101",
    	"DateOfIssue": "2018-06-13T16:02:28-06:00",
    	"Code": "01",
    	"Reason": "Error en la informacion del cliente"
	}],
	"Other": null
}
## Ejemplo del JSON para Factura Electrónica, Tiquete Electrónico y Nota de crédito** (Sin impuesto y con Exoneración)
```json
{
	"CompanyAPI": "78dd8617-c4f0-453b-bd5e-1912f124e731",
	"Environment": "stag",
	"Key": {
		"Branch": "01",
		"Terminal": "1",
		"Type": "01",
		"Voucher": "505",
		"Country": "506",
		"Situation": "1"
	},
	"Header": {
		"Date": "2018-06-20T16:15:21-06:00",
		"TermOfSale": "02",
		"CreditTerm": "15",
		"PaymentMethod": "03"
	},
	"Receiver": {
		"Name": "Los patitos S.A",
		"Identification": {
			"Type": "02",
			"Number": "3101234567"
		},
		"Email": "info@lospatitos.com"
	},
	"Detail": [{
		"Number": "1",
		"Code": {
			"Type": "04",
			"Code": "CONTRL."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Control de acceso Hikvision Voltaje DC 00V/1a",
		"UnitPrice": 213.0,
		"TotalAmount": 213.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 213.0,
		"Tax": null,
		"TotalLineAmount": 240.69
	}, {
		"Number": "2",
		"Code": {
			"Type": "04",
			"Code": "ENRVPN."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys",
		"UnitPrice": 265.0,
		"TotalAmount": 265.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 265.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 34.45,
			"Exoneration": {
				"DocumentType": "01",
				"DocumentNumber": "100",
				"InstitutionName": "Ministerio de Hacienda",
				"IssueDate": "2016-09-26T13:00:00+06:00",
				"TaxAmount": 130,
				"PurchasePercentage": 10
			}
		}],
		"TotalLineAmount": 299.45
	}],
	"Summary": {
		"Currency": "USD",
		"ExchangeRate": 570.31,
		"TotalTaxedService": 478.0,
		"TotalExemptService": 0.0,
		"TotalTaxedGoods": 0.0,
		"TotalExemptGoods": 0.0,
		"TotalTaxed": 478.0,
		"TotalExempt": 0.0,
		"TotalSale": 478.0,
		"TotalDiscounts": 0.0,
		"TotalNetSale": 478.0,
		"TotalTaxes": 62.14,
		"TotalVoucher": 540.14
	},
	"Reference": [{
		"DocumentType": "01",
    	"DocumentNumber": "50631071800310166091900100001010000000108152884101",
    	"DateOfIssue": "2018-06-13T16:02:28-06:00",
    	"Code": "01",
    	"Reason": "Error en la informacion del cliente"
	}],
	"Other": null
}
```
## Ejemplo del JSON para Factura Electrónica, Tiquete Electrónico y Nota de Crédito** (Con Descuento y sin Impuesto)
```json
{
	"CompanyAPI": "78dd8617-c4f0-453b-bd5e-1912f124e731",
	"Environment": "stag",
	"Key": {
		"Branch": "01",
		"Terminal": "1",
		"Type": "01",
		"Voucher": "505",
		"Country": "506",
		"Situation": "1"
	},
	"Header": {
		"Date": "2018-06-20T16:15:21-06:00",
		"TermOfSale": "02",
		"CreditTerm": "15",
		"PaymentMethod": "03"
	},
	"Receiver": {
		"Name": "Los patitos S.A",
		"Identification": {
			"Type": "02",
			"Number": "3101234567"
		},
		"Email": "info@lospatitos.com"
	},
	"Detail": [{
		"Number": "1",
		"Code": {
			"Type": "04",
			"Code": "CONTRL."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Control de acceso Hikvision Voltaje DC 00V/1a",
		"UnitPrice": 213.0,
		"TotalAmount": 213.0,
		"Discount": 21.3,
		"NatureOfDiscount": "Descuento del 10% de ejemplo",
		"SubTotal": 191.7,
		"Tax": null,
		"TotalLineAmount": 191.7
	}, {
		"Number": "2",
		"Code": {
			"Type": "04",
			"Code": "ENRVPN."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys",
		"UnitPrice": 265.0,
		"TotalAmount": 265.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 265.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 34.45,
			"Exoneration": {
				"DocumentType": "01",
				"DocumentNumber": "100",
				"InstitutionName": "Ministerio de Hacienda",
				"IssueDate": "2016-09-26T13:00:00+06:00",
				"TaxAmount": 130,
				"PurchasePercentage": 10
			}
		}],
		"TotalLineAmount": 299.45
	}],
	"Summary": {
		"Currency": "USD",
		"ExchangeRate": 570.31,
		"TotalTaxedService": 478.0,
		"TotalExemptService": 0.0,
		"TotalTaxedGoods": 0.0,
		"TotalExemptGoods": 0.0,
		"TotalTaxed": 478.0,
		"TotalExempt": 0.0,
		"TotalSale": 478.0,
		"TotalDiscounts": 0.0,
		"TotalNetSale": 478.0,
		"TotalTaxes": 62.14,
		"TotalVoucher": 540.14
	},
	"Reference": [{
		"DocumentType": "01",
    	"DocumentNumber": "50631071800310166091900100001010000000108152884101",
    	"DateOfIssue": "2018-06-13T16:02:28-06:00",
    	"Code": "01",
    	"Reason": "Error en la informacion del cliente"
	}],
	"Other": null
}
```
## Ejemplo del JSON para Factura Electrónica, Tiquete Electrónico y Nota de crédito** (Con impuesto y descuento)
```json
{
	"CompanyAPI": "78dd8617-c4f0-453b-bd5e-1912f124e731",
	"Environment": "stag",
	"Key": {
		"Branch": "01",
		"Terminal": "1",
		"Type": "01",
		"Voucher": "505",
		"Country": "506",
		"Situation": "1"
	},
	"Header": {
		"Date": "2018-06-20T16:15:21-06:00",
		"TermOfSale": "02",
		"CreditTerm": "15",
		"PaymentMethod": "03"
	},
	"Receiver": {
		"Name": "Los patitos S.A",
		"Identification": {
			"Type": "02",
			"Number": "3101234567"
		},
		"Email": "info@lospatitos.com"
	},
	"Detail": [{
		"Number": "1",
		"Code": {
			"Type": "04",
			"Code": "CONTRL."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Control de acceso Hikvision Voltaje DC 00V/1a",
		"UnitPrice": 213.0,
		"TotalAmount": 213.0,
		"Discount": 21.3,
		"NatureOfDiscount": "Descuento del 10% por ejemplo",
		"SubTotal": 191.7,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 27.69,
			"Exoneration": null
		}],
		"TotalLineAmount": 219.39
	}, {
		"Number": "2",
		"Code": {
			"Type": "04",
			"Code": "ENRVPN."
		},
		"Quantity": 1.0,
		"UnitOfMeasure": "Sp",
		"CommercialUnitOfMeasure": null,
		"Detail": "Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys",
		"UnitPrice": 265.0,
		"TotalAmount": 265.0,
		"Discount": null,
		"NatureOfDiscount": "",
		"SubTotal": 265.0,
		"Tax": [{
			"Code": "01",
			"Rate": 13.00,
			"Amount": 34.45,
			"Exoneration": {
				"DocumentType": "01",
				"DocumentNumber": "100",
				"InstitutionName": "Ministerio de Hacienda",
				"IssueDate": "2016-09-26T13:00:00+06:00",
				"TaxAmount": 130,
				"PurchasePercentage": 10
			}
		}],
		"TotalLineAmount": 299.45
	}],
	"Summary": {
		"Currency": "USD",
		"ExchangeRate": 570.31,
		"TotalTaxedService": 478.0,
		"TotalExemptService": 0.0,
		"TotalTaxedGoods": 0.0,
		"TotalExemptGoods": 0.0,
		"TotalTaxed": 478.0,
		"TotalExempt": 0.0,
		"TotalSale": 478.0,
		"TotalDiscounts": 0.0,
		"TotalNetSale": 478.0,
		"TotalTaxes": 62.14,
		"TotalVoucher": 540.14
	},
	"Reference": [{
		"DocumentType": "01",
    	"DocumentNumber": "50631071800310166091900100001010000000108152884101",
    	"DateOfIssue": "2018-06-13T16:02:28-06:00",
    	"Code": "01",
    	"Reason": "Error en la informacion del cliente"
	}],
	"Other": null
}
```

***Los ejemplos anteriores aplican igualmente para los tiquetes electrónicos a excepción que el tipo (Type) que se encuentra en el Key debe ser cambiado por "04" según respecta en la tabla #1*
*** Las Notas de crédito deben tener por obligación la referencia a la factura a la que le aplica la acción respectiva según la tabla #7*


## Anexo de tablas

Tablas requeridas para el envio de la Factura Electrónica

### Tabla #1
| Tipo de comprobante o documento asociado | Código |
| --- | :---: |
| Factura electrónica | 01 |
| Nota de débito electrónica | 02 |
| Nota de crédito electrónica | 03 |
| Tiquete Electrónico | 04 |
| Confirmación de aceptación del comprobante electrónico | 05 |
| Confirmación de aceptación parcial del comprobante electrónico | 06 |
| Confirmación de rechazo del comprobante electrónico | 07 |

### Tabla #2

| Condición de la venta | Código |
| --- | :---:
| Contado | 01 
| Crédito | 02 
| Consignación | 03 
| Apartado | 04
| Arrendamiento con opción de compra | 05
| Arrendamiento en función financiera | 06
| Otros (se debe indicar la condición de la venta)| 99

### Tabla #3

| Código | Tipo de identificación | Longitud
| :---: | :---: | --- | 
| 01 | Cedula Física | Debe de contener 9 dígitos, sin cero al inicio y sin guiones.
| 02 | Cedula Jurídica | Debe contener 10 dígitos, sin cero al inicio y sin guiones.
| 03 | DIMEX | Debe contener 11 o 12 dígitos, sin ceros al inicio y sin guiones
| 04 | NITE | Debe contener 10 dígitos, sin ceros al inicio y sin guiones

### Tabla #4

| Tipo de código de producto/servicio | Código
| --- | :---:
| Código del producto del vendedor | 01
| Código del producto del comprador | 02
| Código del producto asignado por la industria | 03
| Código uso interno | 04
| Otros | 99

### Tabla #5

| Impuesto | Código
| --- | :---:
| Impuesto General sobre las Ventas | 01
| Impuesto Selectivo de Consumo | 02
| Impuesto Único a los combustibles | 03
| Impuesto específico de Bebidas Alcohólicas | 04
| Impuesto Específico sobre las bebidas envasadas sin contenido alcohólico y jabones de tocador | 05
| Impuesto a los Productos de Tabaco | 06
| Servicio | 07
| Otros | 98

### Tabla #6

| Exoneración | Código
| --- |:---:
| Impuesto General sobre las Ventas Diplomáticos | 08
| Impuesto General sobre las Ventas Compras Autorizadas | 09
| Impuesto General sobre las ventas Instituciones Públicas y otros Organismos | 10
| Impuesto Selectivo de Consumo Compras Autorizadas | 11
| Otros | 99

### Tabla #7

| Descripción del campo | Código
| --- |:---:
| Anula Documento de Referencia | 01
| Corrige texto documento de referencia | 02
| Corrige monto | 03
| Referencia a otro documento | 04
| Sustituye comprobante provisional por contingencia | 05
| Otros | 99