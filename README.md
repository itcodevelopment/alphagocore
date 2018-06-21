---


---

<h1 id="crear-un-usuario">Crear un Usuario</h1>
<p>Se debera enviar una peticion de tipo <strong>POST</strong> a la siguiente ruta: <strong>/api/users/</strong></p>
<h3 id="datos-requeridos">Datos Requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Name</strong></td>
<td>Nombre de  la persona (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Lastname</strong></td>
<td>Apellido de la persona (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Email</strong></td>
<td>Email de la persona (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Phone</strong></td>
<td>Telefono de contacto (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Username</strong></td>
<td>Usuario para autenticar (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Company_name</strong></td>
<td>Nombre de la compania (<em>String</em>)</td>
</tr>
</tbody>
</table><h3 id="estructura-del-json">Estructura del JSON:</h3>
<pre><code>{
	"Name" : "Pedro",
	"Lastname": "Castillo",
	"Email": "pedro@itcoint.com",
	"Phone": "89586444",
	"Username": "pedro",
	"Password": "Intlog6151$%",
	"Company_name": "ITCO"
}
</code></pre>
<h1 id="login-usuario">Login Usuario</h1>
<p>Se debera enviar una peticio de tipo <strong>POST</strong> a la siguiente ruta:  <strong>/api/users/login</strong></p>
<h3 id="datos-requeridos-1">Datos Requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>username</strong></td>
<td>Nombre de usuario (<em>String</em>)</td>
</tr>
<tr>
<td><strong>password</strong></td>
<td>Contrasena de usuario (<em>String</em>)</td>
</tr>
</tbody>
</table><h3 id="estructura-del-json-1">Estructura del JSON</h3>
<pre><code>{
	"username": "pedro",
	"password": "Intlog6151$%"
}
</code></pre>
<h3 id="respuesta-del-recurso">Respuesta del recurso:</h3>
<p>Esto respondera un SessionKey que sera requerido para algunas peticiones ( Esto se debera guardar en el Local Storage para persistirlo )</p>
<p>El session key tiene una validez de <strong>1 hora</strong> por lo cual despues de este periodo debera solicitarse otro.</p>
<pre><code>{
    "sessionKey": "d1dnMG5RdnQ0YXFwMjczQ3pvdXM4UT09OjoSsfF4d0+BkExpS5YCO32C"
}
</code></pre>
<h1 id="generar-api-key">Generar API Key</h1>
<p>Este API Key que es generado por motivos de seguridad para el uso del API de <strong>Alpha Go Core</strong> y es totalmente diferente al <strong>SessionKey</strong> generado por <strong>CRL</strong></p>
<p>Se debera enviar una peticion de tipo <strong>POST</strong> a la siguiente ruta: <strong>/api/create/token</strong></p>
<h3 id="datos-requeridos-2">Datos Requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Email</strong></td>
<td>Email del usuario registrado (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Password</strong></td>
<td>Password del usuario registrado (<em>String</em>)</td>
</tr>
</tbody>
</table><h3 id="estructura-del-json-2">Estructura del JSON:</h3>
<pre><code>{
	"Email": "pedro@itcoint.com",
	"Password": "Intlog6151$%"
}
</code></pre>
<h3 id="respuesta-del-recurso-1">Respuesta del recurso:</h3>
<pre><code>{
    "apiKey": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk1OTEyMzd9.Pz6pdumUn6_0jthhB0EW0aLt2DPXS1Zi2d6otsx6P6U"
}
</code></pre>
<h1 id="crear-una-compania">Crear una compania</h1>
<p>Se debera enviar una peticion de tipo <strong>POST</strong> a la siguiente ruta: <strong>/api/company</strong></p>
<h3 id="datos-requeridos-3">Datos Requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Name</strong></td>
<td>Nombre de la compania (<em>String</em>)</td>
</tr>
<tr>
<td><strong>CeUser</strong></td>
<td>Usuario de Comprobantes Electronicos (<em>String</em>)</td>
</tr>
<tr>
<td><strong>CePassword</strong></td>
<td>Contrasena de Comprobantes Electronicos (<em>String</em>)</td>
</tr>
<tr>
<td><strong>CePin</strong></td>
<td>Pin de Comprobantes Electronicos (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Environment</strong></td>
<td>Entorno en que se carga el certificado <strong>Stag</strong> - <strong>Prod</strong> (<em>String</em>)</td>
</tr>
<tr>
<td><strong>UserName</strong></td>
<td>Usuario Logueado (<em>String</em>)</td>
</tr>
<tr>
<td><strong>SessionKey</strong></td>
<td>Session Key del usuario logueado (<em>String</em>)</td>
</tr>
<tr>
<td><strong>CrlCertificateCode</strong></td>
<td>Se debe enviar vacio (<em>String</em>)</td>
</tr>
<tr>
<td><strong>FilePath</strong></td>
<td>Se debe enviar vacio (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Cert</strong></td>
<td>Certificado .p12 codificado en <strong>base64</strong> (<em>Base 64 String</em>)</td>
</tr>
</tbody>
</table><p><a href="#crear-un-usuario">Como Crear Un Usuario</a><br>
<a href="#login-usuario">Obtener Session Key</a></p>
<h3 id="estructura-del-json-3">Estructura del Json:</h3>
<p>Todos los campos son requeridos sin excepcion.</p>
<pre><code>{
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
</code></pre>
<h3 id="respuesta-del-recurso-2">Respuesta del recurso:</h3>
<pre><code>{
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
</code></pre>
<h2 id="obtener-todas-las-companias">Obtener todas las companias:</h2>
<p>Para obtener todas las companias, debera enviar una peticion de tipo <strong>GET</strong> a la siguiente ruta: <strong>/api/companies</strong></p>
<h3 id="datos-requeridos-4">Datos requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Authorization</strong></td>
<td>Corresponde al API Key de AGC (<em>String</em>)</td>
</tr>
</tbody>
</table><h3 id="respuesta-del-recurso-3">Respuesta del recurso:</h3>
<pre><code>[
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
</code></pre>
<h2 id="obtener-una-compania">Obtener Una Compania</h2>
<p>Para obtener todas las companias, debera enviar una peticion de tipo <strong>GET</strong> a la siguiente ruta: <strong>/api/company/:id</strong></p>
<h3 id="datos-requeridos-5">Datos requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Authorization</strong></td>
<td>Corresponde al API Key de AGC (<em>String</em>)</td>
</tr>
<tr>
<td><strong>id</strong></td>
<td>Id de la compania que se quiere obtener (<em>Int</em>)</td>
</tr>
</tbody>
</table><h3 id="url-de-ejemplo">URL de ejemplo:</h3>
<p>/api/company/1</p>
<h3 id="respuesta-del-recurso-4">Respuesta del recurso:</h3>
<pre><code>{
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
</code></pre>
<h1 id="token-hacienda">Token Hacienda</h1>
<p>Para generar un token de acceso para hacienda es necesario enviar una solicitud de tipo <strong>POST</strong> a la siguiente ruta: <strong>/api/create/access-token</strong></p>
<h3 id="datos-requeridos-6">Datos Requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>authorization</strong></td>
<td>Esto se envia en el header de la peticion y correspode al APIKEY del usuario Alpha Go Core (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Environment</strong></td>
<td><strong>api-stag</strong> - <strong>api-prod</strong> (<em>String</em>)</td>
</tr>
<tr>
<td><strong>CeUser</strong></td>
<td>Usuario de comprobantes electronicos</td>
</tr>
<tr>
<td><strong>CePassword</strong></td>
<td>Contrasena de comprobantes electronicos</td>
</tr>
</tbody>
</table><h3 id="estructura-del-json-4">Estructura del JSON</h3>
<p>Ejemplo enviado desde NodeJS con Request:</p>
<pre><code>headers: 
   {
     'Content-Type': 'application/json',
      Authorization: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk2MDk2NjB9.9aq0zRpxlKf9NPF7rpZpQ0nKMQ1Zu0mqGDd9_VKpB9I' 
     },
  body: 
   { 
     Environment: 'api-stag',
     CeUser: 'cpj-3-101-660919@stag.comprobanteselectronicos.go.cr',
     CePassword: 'E{ToB(ebW&amp;F?%%!}r!G]' }
  };
</code></pre>
<p><a href="#generar-api-key">Generar autorizacion (API KEY)</a></p>
<h3 id="respuesta-del-recurso-5">Respuesta del recurso:</h3>
<pre><code>{
    "code": 201,
    "accessToken": "eyJhbGciOiJSUzI1NiJ9.eyJqdGkiOiIzNjY0NzAyMS1lYTRkLTQxYjItOTRkNi1hMTMyYzZjMzA0NGIiLCJleHAiOjE1Mjk2MTA3NDUsIm5iZiI6MCwiaWF0IjoxNTI5NjEwNDQ1LCJpc3MiOiJodHRwczovL2lkcC5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IvYXV0aC9yZWFsbXMvcnV0LXN0YWciLCJhdWQiOiJhcGktc3RhZyIsInN1YiI6IjA4YWY1MzI0LTdkYWYtNDhhMC05NTQwLTFjOGRmNzVjNGU4NCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFwaS1zdGFnIiwic2Vzc2lvbl9zdGF0ZSI6ImI3ZmIwOWJhLTNmZWMtNGQxNC05MDYwLWE2M2NkOWFhOWNkMCIsImNsaWVudF9zZXNzaW9uIjoiNDY1ZDZmNzktNTNhOC00YjY0LTllMTktZjhiZTJiNzZiODUzIiwiYWxsb3dlZC1vcmlnaW5zIjpbXSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LXByb2ZpbGUiXX19LCJuYW1lIjoiQUxGQVJPICYgSEVSTkFOREVaIElUIENPUlBPUkFUSU9OIElUQ08gU09DSUVEQUQgQU5PTklNQSAiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJjcGotMy0xMDEtNjYwOTE5QHN0YWcuY29tcHJvYmFudGVzZWxlY3Ryb25pY29zLmdvLmNyIiwiZ2l2ZW5fbmFtZSI6IkFMRkFSTyAmIEhFUk5BTkRFWiBJVCBDT1JQT1JBVElPTiBJVENPIFNPQ0lFREFEIEFOT05JTUEiLCJwb2xpY3ktaWQiOiI1OGE2MjAzMzc2ZWFlMTQwOGNlNWU3ZGQiLCJlbWFpbCI6ImNwai0zLTEwMS02NjA5MTlAc3RhZy5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IifQ.eyGqDfqb4aHw_cA8x2dQCGdaH0Z-qOBFEwHJ15pS2MWqcCti2aw3gC_2riZS9Ss-gI1Q4eTNWpbelo_sRf6-DEvx4P6Q-deDWwgFEzZuQj2srUi6tN36sT25XXtsz-Y2baCmn13cWnfWkrFqKx6Gs4nTw9fXcco21QLpkj4YW8j7l3eFuFHzRj20JR9wqb8ZpNmH2Y9KjYPr9eL2pPPWVMDqt4NeVSARMkbH0I9hD8-s7GIZyUnjpXBQh8kkQ679kNwDpPvbC9h7SRRgKqA6Mn7ZQ0Lvu8XLveyNR4ptOSfYnWn4sgCFwO5oPH1rN6nqT_FkSq7InvoKE0mLZEdTfA",
    "expires": 300
}
</code></pre>
<p>La sección del <em>accessToken</em> es lo importante, ya que eso es lo que enviaremos a hacienda con el resto de infomacion para el envio de los comprobantes y consultas.</p>
<p>El token expira en 300s</p>

