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

