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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"Name"</span> <span class="token punctuation">:</span> <span class="token string">"Pedro"</span><span class="token punctuation">,</span>
	<span class="token string">"Lastname"</span><span class="token punctuation">:</span> <span class="token string">"Castillo"</span><span class="token punctuation">,</span>
	<span class="token string">"Email"</span><span class="token punctuation">:</span> <span class="token string">"pedro@itcoint.com"</span><span class="token punctuation">,</span>
	<span class="token string">"Phone"</span><span class="token punctuation">:</span> <span class="token string">"89586444"</span><span class="token punctuation">,</span>
	<span class="token string">"Username"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span><span class="token punctuation">,</span>
	<span class="token string">"Password"</span><span class="token punctuation">:</span> <span class="token string">"Intlog6151$%"</span><span class="token punctuation">,</span>
	<span class="token string">"Company_name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO"</span>
<span class="token punctuation">}</span>
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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"username"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span><span class="token punctuation">,</span>
	<span class="token string">"password"</span><span class="token punctuation">:</span> <span class="token string">"Intlog6151$%"</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="respuesta-del-recurso">Respuesta del recurso:</h3>
<p>Esto respondera un SessionKey que sera requerido para algunas peticiones ( Esto se debera guardar en el Local Storage para persistirlo )</p>
<p>El session key tiene una validez de <strong>1 hora</strong> por lo cual despues de este periodo debera solicitarse otro.</p>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"sessionKey"</span><span class="token punctuation">:</span> <span class="token string">"d1dnMG5RdnQ0YXFwMjczQ3pvdXM4UT09OjoSsfF4d0+BkExpS5YCO32C"</span>
<span class="token punctuation">}</span>
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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"Email"</span><span class="token punctuation">:</span> <span class="token string">"pedro@itcoint.com"</span><span class="token punctuation">,</span>
	<span class="token string">"Password"</span><span class="token punctuation">:</span> <span class="token string">"Intlog6151$%"</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="respuesta-del-recurso-1">Respuesta del recurso:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"apiKey"</span><span class="token punctuation">:</span> <span class="token string">"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk1OTEyMzd9.Pz6pdumUn6_0jthhB0EW0aLt2DPXS1Zi2d6otsx6P6U"</span>
<span class="token punctuation">}</span>
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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"Name"</span> <span class="token punctuation">:</span> <span class="token string">"ITCO"</span><span class="token punctuation">,</span>
	<span class="token string">"CeUser"</span> <span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
	<span class="token string">"CePassword"</span> <span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
	<span class="token string">"CePin"</span> <span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
	<span class="token string">"UserName"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span><span class="token punctuation">,</span>
	<span class="token string">"SessionKey"</span> <span class="token punctuation">:</span> <span class="token string">"eTIzb3FiZVUrd3g1N0M2TGo0UlFOQT09OjpjNb1uk2xAobi27LntChi8"</span><span class="token punctuation">,</span>
	<span class="token string">"Environmet"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
	<span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
	<span class="token string">"FilePath"</span><span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
	<span class="token string">"Cert"</span><span class="token punctuation">:</span> <span class="token string">"(CERTIFICADO EN BASE64)"</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="respuesta-del-recurso-2">Respuesta del recurso:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"data"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
        <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">4</span><span class="token punctuation">,</span>
        <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO"</span><span class="token punctuation">,</span>
        <span class="token string">"CeUser"</span><span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
        <span class="token string">"CePassword"</span><span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
        <span class="token string">"CePin"</span><span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
        <span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">"c73b93a548371afcdd5b054aa98ec0ba"</span><span class="token punctuation">,</span>
        <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T17:17:10.557Z"</span><span class="token punctuation">,</span>
        <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T17:17:10.557Z"</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token string">"status"</span><span class="token punctuation">:</span> <span class="token number">201</span>
<span class="token punctuation">}</span>
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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">[</span>
    <span class="token punctuation">{</span>
        <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
        <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO"</span><span class="token punctuation">,</span>
        <span class="token string">"CeUser"</span><span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
        <span class="token string">"CePassword"</span><span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
        <span class="token string">"CePin"</span><span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
        <span class="token string">"Environmet"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
        <span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">"7e4f44938a966bbb669aecc0331694bd"</span><span class="token punctuation">,</span>
        <span class="token string">"FilePath"</span><span class="token punctuation">:</span> <span class="token string">"./certs/cert1529615544862.p12"</span><span class="token punctuation">,</span>
        <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:25.300Z"</span><span class="token punctuation">,</span>
        <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:25.300Z"</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>
        <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span>
        <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"TS"</span><span class="token punctuation">,</span>
        <span class="token string">"CeUser"</span><span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
        <span class="token string">"CePassword"</span><span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
        <span class="token string">"CePin"</span><span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
        <span class="token string">"Environmet"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
        <span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">"70348e40ed539e03caf0f0c00a3732ab"</span><span class="token punctuation">,</span>
        <span class="token string">"FilePath"</span><span class="token punctuation">:</span> <span class="token string">"./certs/cert1529615561259.p12"</span><span class="token punctuation">,</span>
        <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:41.696Z"</span><span class="token punctuation">,</span>
        <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:41.696Z"</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">]</span>
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
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
    <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO"</span><span class="token punctuation">,</span>
    <span class="token string">"CeUser"</span><span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
    <span class="token string">"CePassword"</span><span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
    <span class="token string">"CePin"</span><span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
    <span class="token string">"Environmet"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
    <span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">"7e4f44938a966bbb669aecc0331694bd"</span><span class="token punctuation">,</span>
    <span class="token string">"FilePath"</span><span class="token punctuation">:</span> <span class="token string">"./certs/cert1529615544862.p12"</span><span class="token punctuation">,</span>
    <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:25.300Z"</span><span class="token punctuation">,</span>
    <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-21T21:12:25.300Z"</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="asignar-un-usuario-a-una-compañía">Asignar un usuario a una compañía</h2>
<p>Un usuario puede pertenecer a una o más compañías, por lo tanto para asignar a un usuario a una compañía se deberá realizar por medio de un <strong>POST</strong> a la siguiente ruta: <strong>/api/company/user</strong></p>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"userId"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
	<span class="token string">"companyId"</span><span class="token punctuation">:</span> <span class="token number">6</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="respuesta-del-recurso-5">Respuesta del recurso:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">[</span>
    <span class="token punctuation">{</span>
        <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
        <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"Pedro"</span><span class="token punctuation">,</span>
        <span class="token string">"Lastname"</span><span class="token punctuation">:</span> <span class="token string">"Castillo"</span><span class="token punctuation">,</span>
        <span class="token string">"Email"</span><span class="token punctuation">:</span> <span class="token string">"pedro@itcoint.com"</span><span class="token punctuation">,</span>
        <span class="token string">"Phone"</span><span class="token punctuation">:</span> <span class="token string">"89586444"</span><span class="token punctuation">,</span>
        <span class="token string">"Username"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span><span class="token punctuation">,</span>
        <span class="token string">"Password"</span><span class="token punctuation">:</span> <span class="token string">"Intlog6151$%"</span><span class="token punctuation">,</span>
        <span class="token string">"Company_name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO"</span><span class="token punctuation">,</span>
        <span class="token string">"ApiToken"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
        <span class="token string">"CrlSessionToken"</span><span class="token punctuation">:</span> <span class="token string">"QU03NWd3ZXJMbHFGS1JxODJESDdFQT09Ojo14U7qQYGk+53I3xb57Qw6"</span><span class="token punctuation">,</span>
        <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-29T17:09:18.956Z"</span><span class="token punctuation">,</span>
        <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-07-02T15:28:02.814Z"</span><span class="token punctuation">,</span>
        <span class="token string">"Companies"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span>
            <span class="token punctuation">{</span>
                <span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span>
                <span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"TS"</span><span class="token punctuation">,</span>
                <span class="token string">"CeUser"</span><span class="token punctuation">:</span> <span class="token string">"prueba"</span><span class="token punctuation">,</span>
                <span class="token string">"CePassword"</span><span class="token punctuation">:</span> <span class="token string">"123"</span><span class="token punctuation">,</span>
                <span class="token string">"CePin"</span><span class="token punctuation">:</span> <span class="token string">"1234"</span><span class="token punctuation">,</span>
                <span class="token string">"Environmet"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
                <span class="token string">"CrlCertificateCode"</span><span class="token punctuation">:</span> <span class="token string">"630360f1270cb832a395f0f16dd2c174"</span><span class="token punctuation">,</span>
                <span class="token string">"FilePath"</span><span class="token punctuation">:</span> <span class="token string">"./certs/cert1530292769727.p12"</span><span class="token punctuation">,</span>
                <span class="token string">"CompanyAPI"</span><span class="token punctuation">:</span> <span class="token string">"ff191b1d-f2c8-4140-9402-33d3f0bf4c8e"</span><span class="token punctuation">,</span>
                <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-29T17:19:30.217Z"</span><span class="token punctuation">,</span>
                <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-29T17:19:30.217Z"</span><span class="token punctuation">,</span>
                <span class="token string">"UserCompanies"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
                    <span class="token string">"createdAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-07-02T16:00:57.145Z"</span><span class="token punctuation">,</span>
                    <span class="token string">"updatedAt"</span><span class="token punctuation">:</span> <span class="token string">"2018-07-02T16:00:57.145Z"</span><span class="token punctuation">,</span>
                    <span class="token string">"CompanyId"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span>
                    <span class="token string">"UserId"</span><span class="token punctuation">:</span> <span class="token number">1</span>
                <span class="token punctuation">}</span>
            <span class="token punctuation">}</span>
        <span class="token punctuation">]</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<p>Este mismo devolverá la información del usuario con las compañías a las que pertenece.</p>
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
<pre class=" language-js"><code class="prism  language-js">headers<span class="token punctuation">:</span> 
   <span class="token punctuation">{</span>
      Content<span class="token operator">-</span>Type<span class="token punctuation">:</span> <span class="token string">'application/json'</span><span class="token punctuation">,</span>
      Authorization<span class="token punctuation">:</span> <span class="token string">'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyT2JqIjp7InVzZXIiOiJwZWRybyIsInNlY3JldCI6IkludGxvZzYxNTEkJSJ9LCJpYXQiOjE1Mjk2MDk2NjB9.9aq0zRpxlKf9NPF7rpZpQ0nKMQ1Zu0mqGDd9_VKpB9I'</span> 
     <span class="token punctuation">}</span><span class="token punctuation">,</span>
  body<span class="token punctuation">:</span> 
   <span class="token punctuation">{</span> 
     Environment<span class="token punctuation">:</span> <span class="token string">'api-stag'</span><span class="token punctuation">,</span>
     CeUser<span class="token punctuation">:</span> <span class="token string">'cpj-3-101-660919@stag.comprobanteselectronicos.go.cr'</span><span class="token punctuation">,</span>
     CePassword<span class="token punctuation">:</span> <span class="token string">'E{ToB(ebW&amp;F?%%!}r!G]'</span> <span class="token punctuation">}</span>
  <span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<p><a href="#generar-api-key">Generar autorizacion (API KEY)</a></p>
<h3 id="respuesta-del-recurso-6">Respuesta del recurso:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"code"</span><span class="token punctuation">:</span> <span class="token number">201</span><span class="token punctuation">,</span>
    <span class="token string">"accessToken"</span><span class="token punctuation">:</span> <span class="token string">"eyJhbGciOiJSUzI1NiJ9.eyJqdGkiOiIzNjY0NzAyMS1lYTRkLTQxYjItOTRkNi1hMTMyYzZjMzA0NGIiLCJleHAiOjE1Mjk2MTA3NDUsIm5iZiI6MCwiaWF0IjoxNTI5NjEwNDQ1LCJpc3MiOiJodHRwczovL2lkcC5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IvYXV0aC9yZWFsbXMvcnV0LXN0YWciLCJhdWQiOiJhcGktc3RhZyIsInN1YiI6IjA4YWY1MzI0LTdkYWYtNDhhMC05NTQwLTFjOGRmNzVjNGU4NCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFwaS1zdGFnIiwic2Vzc2lvbl9zdGF0ZSI6ImI3ZmIwOWJhLTNmZWMtNGQxNC05MDYwLWE2M2NkOWFhOWNkMCIsImNsaWVudF9zZXNzaW9uIjoiNDY1ZDZmNzktNTNhOC00YjY0LTllMTktZjhiZTJiNzZiODUzIiwiYWxsb3dlZC1vcmlnaW5zIjpbXSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LXByb2ZpbGUiXX19LCJuYW1lIjoiQUxGQVJPICYgSEVSTkFOREVaIElUIENPUlBPUkFUSU9OIElUQ08gU09DSUVEQUQgQU5PTklNQSAiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJjcGotMy0xMDEtNjYwOTE5QHN0YWcuY29tcHJvYmFudGVzZWxlY3Ryb25pY29zLmdvLmNyIiwiZ2l2ZW5fbmFtZSI6IkFMRkFSTyAmIEhFUk5BTkRFWiBJVCBDT1JQT1JBVElPTiBJVENPIFNPQ0lFREFEIEFOT05JTUEiLCJwb2xpY3ktaWQiOiI1OGE2MjAzMzc2ZWFlMTQwOGNlNWU3ZGQiLCJlbWFpbCI6ImNwai0zLTEwMS02NjA5MTlAc3RhZy5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IifQ.eyGqDfqb4aHw_cA8x2dQCGdaH0Z-qOBFEwHJ15pS2MWqcCti2aw3gC_2riZS9Ss-gI1Q4eTNWpbelo_sRf6-DEvx4P6Q-deDWwgFEzZuQj2srUi6tN36sT25XXtsz-Y2baCmn13cWnfWkrFqKx6Gs4nTw9fXcco21QLpkj4YW8j7l3eFuFHzRj20JR9wqb8ZpNmH2Y9KjYPr9eL2pPPWVMDqt4NeVSARMkbH0I9hD8-s7GIZyUnjpXBQh8kkQ679kNwDpPvbC9h7SRRgKqA6Mn7ZQ0Lvu8XLveyNR4ptOSfYnWn4sgCFwO5oPH1rN6nqT_FkSq7InvoKE0mLZEdTfA"</span><span class="token punctuation">,</span>
    <span class="token string">"expires"</span><span class="token punctuation">:</span> <span class="token number">300</span>
<span class="token punctuation">}</span>
</code></pre>
<h1 id="obtener-token-de-hacienda-por-medio-de-una-funcion-asincrona">Obtener Token de hacienda por medio de una funcion asincrona</h1>
<p>Se puede obtener un token de hacienda por medio de la llamada de una funcion asincrona.</p>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">const</span>  generic  <span class="token operator">=</span>  <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"./controllers/generic-functions"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">let</span>  datos  <span class="token operator">=</span> <span class="token punctuation">{</span>
	Environment<span class="token punctuation">:</span>  <span class="token string">'api-stag'</span><span class="token punctuation">,</span>
	CeUser<span class="token punctuation">:</span>  <span class="token string">'cpj-3-101-660919@stag.comprobanteselectronicos.go.cr'</span><span class="token punctuation">,</span>
	CePassword<span class="token punctuation">:</span>  <span class="token string">'E{ToB(ebW&amp;F?%%!}r!G]'</span>
<span class="token punctuation">}</span>

generic<span class="token punctuation">.</span><span class="token function">getTaxationToken</span><span class="token punctuation">(</span>datos<span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span>data<span class="token punctuation">)</span><span class="token operator">=&gt;</span><span class="token punctuation">{</span>
	console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>data<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="respuesta-de-la-funcion-en-data">Respuesta de la funcion en data:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span> code<span class="token punctuation">:</span> <span class="token number">201</span><span class="token punctuation">,</span>
  accessToken<span class="token punctuation">:</span> <span class="token string">'eyJhbGciOiJSUzI1NiJ9.eyJqdGkiOiJkNTdhODMxMS1iZTc0LTQ3YmQtYjczMi1lNWNkNGVlOGU3MjgiLCJleHAiOjE1Mjk5NjE5MTksIm5iZiI6MCwiaWF0IjoxNTI5OTYxNjE5LCJpc3MiOiJodHRwczovL2lkcC5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IvYXV0aC9yZWFsbXMvcnV0LXN0YWciLCJhdWQiOiJhcGktc3RhZyIsInN1YiI6IjA4YWY1MzI0LTdkYWYtNDhhMC05NTQwLTFjOGRmNzVjNGU4NCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFwaS1zdGFnIiwic2Vzc2lvbl9zdGF0ZSI6ImU2Mzg5ZDQ0LTk1N2EtNDUxYi1hNTdmLWY2ZmNlZmY3MWZjOCIsImNsaWVudF9zZXNzaW9uIjoiZjJjMjVhMGYtYWMyZi00YzFhLWIwMWUtZGU3ZGYyMDU0OTUxIiwiYWxsb3dlZC1vcmlnaW5zIjpbXSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LXByb2ZpbGUiXX19LCJuYW1lIjoiQUxGQVJPICYgSEVSTkFOREVaIElUIENPUlBPUkFUSU9OIElUQ08gU09DSUVEQUQgQU5PTklNQSAiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJjcGotMy0xMDEtNjYwOTE5QHN0YWcuY29tcHJvYmFudGVzZWxlY3Ryb25pY29zLmdvLmNyIiwiZ2l2ZW5fbmFtZSI6IkFMRkFSTyAmIEhFUk5BTkRFWiBJVCBDT1JQT1JBVElPTiBJVENPIFNPQ0lFREFEIEFOT05JTUEiLCJwb2xpY3ktaWQiOiI1OGE2MjAzMzc2ZWFlMTQwOGNlNWU3ZGQiLCJlbWFpbCI6ImNwai0zLTEwMS02NjA5MTlAc3RhZy5jb21wcm9iYW50ZXNlbGVjdHJvbmljb3MuZ28uY3IifQ.Z2e-iUyojjM0CVbhNCMqLoE9XfunGO6l-vP7FktRR0ucZQA5U_UkJGqk54sBym2Qmbg8S1cXLKzEb7p6MJRW5EiXgkvtpWxv4QcTZDNcPAcLxYhoE9iOHRNI_crBhHcGKf_Jbl1sAxbY3NA1BKVCMoBmkIDFo7KqrJ36qyWT8JD2V7f9Y2PVo6A79ZsWi-ly0F3ebGZ2gC72S09xq2ES4J7DrOifr_-oDrP9TDGY0i-rIAF7mUby4ri-90gUAAe8Mt0DgBiu2m6aFh3WePDgHKdoQODcHOWXFZO01EpokkukgUjXzqv8D0kz3unfI7cIa8SfNeDlOYUKqQr8QuyRCA'</span><span class="token punctuation">,</span>
  expires<span class="token punctuation">:</span> <span class="token number">300</span> <span class="token punctuation">}</span>
</code></pre>
<p>La sección del <em>accessToken</em> es lo importante, ya que eso es lo que enviaremos a hacienda con el resto de infomacion para el envio de los comprobantes y consultas.</p>
<p>El token expira en 300s</p>
<h1 id="clave-para-firmar-documentos">Clave para firmar documentos</h1>
<p>Para generar una clave que previamente puede ser utilizada para firmar los diferentes tipos de documentos xml se debe enviar una peticion de tipo <strong>POST</strong> a la siguiente ruta : <strong>/api/generate/document-key</strong></p>
<h3 id="datos-requeridos-7">Datos requeridos:</h3>

<table>
<thead>
<tr>
<th>Clave</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>TipoDocumento</strong></td>
<td>FE - ND - NC - TE - CCE - CPCE - RCE (<em>String</em>)</td>
</tr>
<tr>
<td><strong>TipoCedula</strong></td>
<td>fisico - juridico (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Cedula</strong></td>
<td>Numero de cedula sin guiones (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Situacion</strong></td>
<td>normal - contingencia - sininternet (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Consecutivo</strong></td>
<td>Consecutivo de factura sin letras (Solo digitos) (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Codigo de Seguridad</strong></td>
<td>codigo de 8 numeros (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Terminal</strong></td>
<td>Numero de terminal (<em>String</em>)</td>
</tr>
<tr>
<td><strong>Sucursal</strong></td>
<td>Numero de sucursal (<em>String</em>)</td>
</tr>
<tr>
<td><strong>SessionKey</strong></td>
<td>SessionKey del usuario logueado (<em>String</em>)</td>
</tr>
<tr>
<td><strong>User</strong></td>
<td>Nombre de usuario logueado</td>
</tr>
</tbody>
</table><p>Nota: <strong>Terminal</strong> y <strong>Sucursal</strong>  son campos opcionales y pueden no ser enviados.</p>
<h3 id="estrucuctura-del-json">Estrucuctura del JSON:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"TipoCedula"</span><span class="token punctuation">:</span> <span class="token string">"fisico"</span><span class="token punctuation">,</span>
	<span class="token string">"Cedula"</span><span class="token punctuation">:</span> <span class="token string">"118470589"</span><span class="token punctuation">,</span>
	<span class="token string">"Situacion"</span><span class="token punctuation">:</span> <span class="token string">"normal"</span><span class="token punctuation">,</span>
	<span class="token string">"CodigoPais"</span><span class="token punctuation">:</span> <span class="token string">"506"</span><span class="token punctuation">,</span>
	<span class="token string">"Consecutivo"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
	<span class="token string">"CodigoSeguridad"</span><span class="token punctuation">:</span> <span class="token string">"01010101"</span><span class="token punctuation">,</span>
	<span class="token string">"TipoDocumento"</span><span class="token punctuation">:</span> <span class="token string">"FE"</span><span class="token punctuation">,</span>
	<span class="token string">"SessionKey"</span><span class="token punctuation">:</span> <span class="token string">"SHhnbGtVSEJlV3BCUlhFcFI4RE4xdz09OjpquPlO+d01kO61acnZrtBE"</span><span class="token punctuation">,</span>
	<span class="token string">"User"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="respuesta-del-recurso-7">Respuesta del recurso:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
    <span class="token string">"code"</span><span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span>
    <span class="token string">"msg"</span><span class="token punctuation">:</span> <span class="token string">"ok"</span><span class="token punctuation">,</span>
    <span class="token string">"data"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
        <span class="token string">"clave"</span><span class="token punctuation">:</span> <span class="token string">"50625061800011847058900100001010000000001101010101"</span><span class="token punctuation">,</span>
        <span class="token string">"consecutivo"</span><span class="token punctuation">:</span> <span class="token string">"00100001010000000001"</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h1 id="crear-clave-por-medio-de-una-funcion">Crear clave por medio de una funcion</h1>
<p>Si la clave no se desea obtener por medio del endpoint, se puede obtener mediante el codigo de la siguiente manera:</p>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">const</span> generic <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"./controllers/generic-functions"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">let</span> datos <span class="token operator">=</span> <span class="token punctuation">{</span>
    <span class="token string">"TipoCedula"</span><span class="token punctuation">:</span> <span class="token string">"fisico"</span><span class="token punctuation">,</span>
    <span class="token string">"Cedula"</span><span class="token punctuation">:</span> <span class="token string">"118470589"</span><span class="token punctuation">,</span>
    <span class="token string">"Situacion"</span><span class="token punctuation">:</span> <span class="token string">"normal"</span><span class="token punctuation">,</span>
    <span class="token string">"CodigoPais"</span><span class="token punctuation">:</span> <span class="token string">"506"</span><span class="token punctuation">,</span>
    <span class="token string">"Consecutivo"</span><span class="token punctuation">:</span> <span class="token string">"10203040"</span><span class="token punctuation">,</span>
    <span class="token string">"CodigoSeguridad"</span><span class="token punctuation">:</span> <span class="token string">"01010101"</span><span class="token punctuation">,</span>
    <span class="token string">"TipoDocumento"</span><span class="token punctuation">:</span> <span class="token string">"RCE"</span><span class="token punctuation">,</span>
    <span class="token string">"SessionKey"</span><span class="token punctuation">:</span> <span class="token string">"RlpaekZBZnluV0wrZkpLYkVkQVFxZz09OjqYXJ8pAjr0MSx33bgs2Pcf"</span><span class="token punctuation">,</span>
    <span class="token string">"User"</span><span class="token punctuation">:</span> <span class="token string">"pedro"</span>
<span class="token punctuation">}</span>

generic<span class="token punctuation">.</span><span class="token function">documentKey</span><span class="token punctuation">(</span>datos<span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span>data<span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
    console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>data<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="retorna-el-siguiente-valor-en-data">Retorna el siguiente valor en data:</h3>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span> code<span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span>
  msg<span class="token punctuation">:</span> <span class="token string">'ok'</span><span class="token punctuation">,</span>
  data<span class="token punctuation">:</span>
	 <span class="token punctuation">{</span> 
	     clave<span class="token punctuation">:</span> <span class="token string">'50625061800011847058900100001070010203040101010101'</span><span class="token punctuation">,</span>
         consecutivo<span class="token punctuation">:</span> <span class="token string">'00100001070010203040'</span>
     <span class="token punctuation">}</span> 
<span class="token punctuation">}</span>
</code></pre>
<h1 id="crear-factura">Crear Factura</h1>
<p>Se debe de enviar una petición de tipo <strong>POST</strong> a la siguiente ruta: <strong>/api/invoice</strong></p>
<h2 id="datos-requeridos-8">Datos requeridos</h2>
<ul>
<li>
<p><strong>CompanyAPI:</strong> Id de la compañía creada</p>
</li>
<li>
<p><strong>Environment:</strong> Ambiente en el que se envía la factura</p>
</li>
<li>
<p><strong>Key</strong></p>
<ul>
<li>
<p><strong>Branch:</strong> Numero de la sucursal donde se crea el documento</p>
<blockquote>
<p>Máximo 3 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Terminal:</strong> Numero de la terminal donde se crea el documento</p>
<blockquote>
<p>Máximo 5 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Type:</strong> Tipo de documento</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #01.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Voucher:</strong> Numero consecutivo del comprobante</p>
<blockquote>
<p>Máximo 10 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Country:</strong> Código de país</p>
<blockquote>
<p>3 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Day:</strong> Día del mes de emisión del documento</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Month:</strong> Mes del año de emisión del documento</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Year:</strong> Año de emisión del documento</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Situation:</strong> Situación de presentación del documento</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #01.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>SecuryCode:</strong> Código numérico (aleatorios) generado por el sistema</p>
<blockquote>
<p>Máximo 8 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Header</strong></p>
<ul>
<li>
<p><strong>Date:</strong> Fecha de creación del documento</p>
<blockquote>
<p>YYYY-MM-DDThh:mi:ss[Z|(+|-)hh:mm]. Ejemplo: 2016-09-26T13:00:00+06:00.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TermOfSale:</strong> Condición de venta</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #02.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>CreditTerm:</strong> Plazo del crédito.</p>
<blockquote>
<p>En caso de contado “0”.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>PaymentMethod:</strong> Medio de pago de la factura</p>
<blockquote>
<p><strong>Requerido para Factura Electrónica y Tiquete Electrónico.</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Issuer</strong></p>
<ul>
<li>
<p><strong>Name:</strong> Nombre o razón social del emisor</p>
<blockquote>
<p>Máximo 80 caracteres.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Identification</strong></p>
<ul>
<li>
<p><strong>Type :</strong> Tipo de identificación del emisor</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #03.<br>
Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Number:</strong> Número de cédula física/jurídica/NITE/DIMEX del emisor</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #03.<br>
Máximo 12 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>TradeName:</strong> Nombre comercial del emisor</p>
</li>
<li>
<p><strong>Location</strong></p>
<ul>
<li>
<p><strong>Province:</strong> Provincia del emisor</p>
<blockquote>
<p>Máximo 1 digito.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Canton:</strong> Cantón del emisor</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>District:</strong> Distrito del emisor</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Neighborhood:</strong> Barrio del emisor</p>
<blockquote>
<p>Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Address:</strong> Otras señas de la dirección del emisor</p>
<blockquote>
<p>Máximo 160 caracteres.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Phone</strong></p>
<ul>
<li>
<p><strong>CountryCode:</strong> Código de país</p>
<blockquote>
<p>3 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Number:</strong> Número de teléfono</p>
<blockquote>
<p>Máximo 20 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Email:</strong> Correo electrónico del emisor</p>
<blockquote>
<p>\s*\w+([-+.’]\w+)<em>@\w+([-.]\w+)</em>.\w+([-.]\w+)<em>\s</em>.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Receiver</strong></p>
<ul>
<li>
<p><strong>Name:</strong> Nombre o razón social del receptor</p>
<blockquote>
<p>Máximo 80 caracteres.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Identification</strong></p>
<ul>
<li>
<p><strong>Type:</strong> Tipo de identificación del receptor</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #03.<br>
Máximo 2 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Number:</strong> Número de cédula física/jurídica/NITE/DIMEX del receptor</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #03.<br>
Máximo 12 dígitos.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Email:</strong> Correo electrónico del receptor</p>
<blockquote>
<p>\s*\w+([-+.’]\w+)<em>@\w+([-.]\w+)</em>.\w+([-.]\w+)<em>\s</em>.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Detail</strong></p>
<ul>
<li>
<p><strong>0</strong></p>
<blockquote>
<p>Máximo 1000 líneas por documento.</p>
</blockquote>
<ul>
<li>
<p><strong>Number:</strong> Numero de línea</p>
<blockquote>
<p><strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Code</strong></p>
<ul>
<li>
<p><strong>Type:</strong> Tipo de Código de producto/servicio</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
Máximo 2 digitos<br>
Ver Anexo de Tablas. Tabla #04<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Code:</strong> Código</p>
<blockquote>
<p>Máximo 20 caracteres<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
<li>
<p><strong>Quantity:</strong> Cantidad</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>UnitOfMeasure:</strong> Código de la unidad de medida</p>
<blockquote>
<p><strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>CommercialUnitOfMeasure:</strong> Nombre comercial de la unidad de medida</p>
<blockquote>
<p>Máximo 20 caracteres</p>
</blockquote>
</li>
<li>
<p><strong>Detail:</strong> Detalle de la mercancía transferida o servicio prestado</p>
<blockquote>
<p>Máximo 160 caracteres<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>UnitPrice:</strong> Precio Unitario</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalAmount:</strong> Monto total de la multiplicación de la cantidad por el precio unitario</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Discount:</strong> Monto de descuentos concedidos</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales</p>
</blockquote>
</li>
<li>
<p><strong>NatureOfDiscount:</strong> Descripción del descuento concedido</p>
<blockquote>
<p>Máximo 80 caracteres<br>
<strong>Requerido si aplica descuento</strong></p>
</blockquote>
</li>
<li>
<p><strong>SubTotal:</strong> Se obtiene de la resta del campo “monto total” menos “monto de descuento concedido"</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Tax</strong></p>
<ul>
<li><strong>0</strong>
<ul>
<li>
<p><strong>Code:</strong> Código del impuesto</p>
<blockquote>
<p>Ver Anexo de Tablas. Tabla #05<br>
2 dígitos<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Rate:</strong> Porcentaje del impuesto</p>
<blockquote>
<p>Número decimal compuesto por 4 enteros y 2 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Amount:</strong> Monto del impuesto. Se obtiene de la multiplicación del campo subtotal por la tarifa</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 5 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>Exoneration</strong></p>
<ul>
<li><strong>DocumentType:</strong> Tipo de documento de exoneración o de autorización
<blockquote>
<p>Ver Anexo de Tablas. Tabla #06<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li><strong>DocumentNumber:</strong> Número de documento de exoneración o de autorización
<blockquote>
<p>Máximo 17 caracteres<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li><strong>InstitutionName:</strong> Nombre de la institución a la que estamos exonerando
<blockquote>
<p>Máximo 80 caracteres<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li><strong>IssueDate:</strong> Fecha de emisión del documento de exoneración o de autorización
<blockquote>
<p>YYYY-MM-DDThh:mi:ss[Z|(+|-)hh:mm]. Ejemplo: 2016-09-26T13:00:00+06:00.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li><strong>TaxAmount:</strong> Monto del impuesto Exonerado o autorizado sin impuesto
<blockquote>
<p>Número decimal compuesto por 13 enteros y 5 decimales.<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li><strong>PurchasePercentage:</strong> Porcentaje de la compra autorizada o exoneración
<blockquote>
<p>Máximo 3 dígitos<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>TotalLineAmount:</strong> Total por línea de detalle. Se obtiene de la suma de los campos “subtotal” mas “monto del impuesto”</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Summary</strong></p>
<ul>
<li>
<p><strong>Currency:</strong> Código de la moneda</p>
<blockquote>
<p>3 caracteres<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>ExchangeRate:</strong> Tipo de cambio</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalTaxedService:</strong> Total servicios gravados con IV</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalExemptService:</strong> Total servicios exentos de IV</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalTaxedGoods:</strong> Total mercadería gravada con IV</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalExemptGoods:</strong> Total mercadería exenta de IV</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalTaxed:</strong> Total gravado</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalExempt:</strong> Total exento</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalSale:</strong> Total de venta</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalDiscounts:</strong> Total descuentos</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalNetSale:</strong> Total de venta neta</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalTaxes:</strong> Total de impuestos</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
<li>
<p><strong>TotalVoucher:</strong> Total de comprobante</p>
<blockquote>
<p>Número decimal compuesto por 13 enteros y 3 decimales<br>
<strong>Requerido</strong></p>
</blockquote>
</li>
</ul>
<h2 id="ejemplo-del-json">Ejemplo del JSON</h2>
</li>
</ul>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"CompanyAPI"</span><span class="token punctuation">:</span> <span class="token string">"78dd8617-c4f0-453b-bd5e-1912f124e731"</span><span class="token punctuation">,</span>
	<span class="token string">"Environment"</span><span class="token punctuation">:</span> <span class="token string">"stag"</span><span class="token punctuation">,</span>
	<span class="token string">"Key"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token string">"Branch"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
		<span class="token string">"Terminal"</span><span class="token punctuation">:</span> <span class="token string">"1"</span><span class="token punctuation">,</span>
		<span class="token string">"Type"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
		<span class="token string">"Voucher"</span><span class="token punctuation">:</span> <span class="token string">"505"</span><span class="token punctuation">,</span>
		<span class="token string">"Country"</span><span class="token punctuation">:</span> <span class="token string">"506"</span><span class="token punctuation">,</span>
		<span class="token string">"Situation"</span><span class="token punctuation">:</span> <span class="token string">"1"</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"Header"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token string">"Date"</span><span class="token punctuation">:</span> <span class="token string">"2018-06-20T16:15:21-06:00"</span><span class="token punctuation">,</span>
		<span class="token string">"TermOfSale"</span><span class="token punctuation">:</span> <span class="token string">"02"</span><span class="token punctuation">,</span>
		<span class="token string">"CreditTerm"</span><span class="token punctuation">:</span> <span class="token string">"15"</span><span class="token punctuation">,</span>
		<span class="token string">"PaymentMethod"</span><span class="token punctuation">:</span> <span class="token string">"03"</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"Issuer"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"ITCO S.A"</span><span class="token punctuation">,</span>
		<span class="token string">"Identification"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"Type"</span><span class="token punctuation">:</span> <span class="token string">"02"</span><span class="token punctuation">,</span>
			<span class="token string">"Number"</span><span class="token punctuation">:</span> <span class="token string">"3101660919"</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"TradeName"</span><span class="token punctuation">:</span> <span class="token string">"ITCO S.A."</span><span class="token punctuation">,</span>
		<span class="token string">"Location"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"Province"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
			<span class="token string">"Canton"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
			<span class="token string">"District"</span><span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
			<span class="token string">"Neighborhood"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
			<span class="token string">"Address"</span><span class="token punctuation">:</span> <span class="token string">"DEL COLEGIO DE ABOGADOS, 100M SUR Y 250M OESTE. EDIFICIO CAGIOCA."</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"Phone"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"CountryCode"</span><span class="token punctuation">:</span> <span class="token number">506</span><span class="token punctuation">,</span>
			<span class="token string">"Number"</span><span class="token punctuation">:</span> <span class="token string">"22516262"</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"Email"</span><span class="token punctuation">:</span> <span class="token string">"info@itcoint.com"</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"Receiver"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token string">"Name"</span><span class="token punctuation">:</span> <span class="token string">"Los patitos S.A"</span><span class="token punctuation">,</span>
		<span class="token string">"Identification"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"Type"</span><span class="token punctuation">:</span> <span class="token string">"02"</span><span class="token punctuation">,</span>
			<span class="token string">"Number"</span><span class="token punctuation">:</span> <span class="token string">"3101234567"</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"Email"</span><span class="token punctuation">:</span> <span class="token string">"info@lospatitos.com"</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"Detail"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token punctuation">{</span>
		<span class="token string">"Number"</span><span class="token punctuation">:</span> <span class="token string">"1"</span><span class="token punctuation">,</span>
		<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"Type"</span><span class="token punctuation">:</span> <span class="token string">"04"</span><span class="token punctuation">,</span>
			<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token string">"CONTRL."</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"Quantity"</span><span class="token punctuation">:</span> <span class="token number">1.0</span><span class="token punctuation">,</span>
		<span class="token string">"UnitOfMeasure"</span><span class="token punctuation">:</span> <span class="token string">"Sp"</span><span class="token punctuation">,</span>
		<span class="token string">"CommercialUnitOfMeasure"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
		<span class="token string">"Detail"</span><span class="token punctuation">:</span> <span class="token string">"Control de acceso Hikvision Voltaje DC 00V/1a"</span><span class="token punctuation">,</span>
		<span class="token string">"UnitPrice"</span><span class="token punctuation">:</span> <span class="token number">213.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalAmount"</span><span class="token punctuation">:</span> <span class="token number">213.0</span><span class="token punctuation">,</span>
		<span class="token string">"Discount"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
		<span class="token string">"NatureOfDiscount"</span><span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
		<span class="token string">"SubTotal"</span><span class="token punctuation">:</span> <span class="token number">213.0</span><span class="token punctuation">,</span>
		<span class="token string">"Tax"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token punctuation">{</span>
			<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
			<span class="token string">"Rate"</span><span class="token punctuation">:</span> <span class="token number">13.00</span><span class="token punctuation">,</span>
			<span class="token string">"Amount"</span><span class="token punctuation">:</span> <span class="token number">27.69</span><span class="token punctuation">,</span>
			<span class="token string">"Exoneration"</span><span class="token punctuation">:</span> <span class="token keyword">null</span>
		<span class="token punctuation">}</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
		<span class="token string">"TotalLineAmount"</span><span class="token punctuation">:</span> <span class="token number">240.69</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span>
		<span class="token string">"Number"</span><span class="token punctuation">:</span> <span class="token string">"2"</span><span class="token punctuation">,</span>
		<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"Type"</span><span class="token punctuation">:</span> <span class="token string">"04"</span><span class="token punctuation">,</span>
			<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token string">"ENRVPN."</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token string">"Quantity"</span><span class="token punctuation">:</span> <span class="token number">1.0</span><span class="token punctuation">,</span>
		<span class="token string">"UnitOfMeasure"</span><span class="token punctuation">:</span> <span class="token string">"Sp"</span><span class="token punctuation">,</span>
		<span class="token string">"CommercialUnitOfMeasure"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
		<span class="token string">"Detail"</span><span class="token punctuation">:</span> <span class="token string">"Enrutador Vpn Conmutador de 4 puertos Gige Doble banda Linksys"</span><span class="token punctuation">,</span>
		<span class="token string">"UnitPrice"</span><span class="token punctuation">:</span> <span class="token number">265.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalAmount"</span><span class="token punctuation">:</span> <span class="token number">265.0</span><span class="token punctuation">,</span>
		<span class="token string">"Discount"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
		<span class="token string">"NatureOfDiscount"</span><span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
		<span class="token string">"SubTotal"</span><span class="token punctuation">:</span> <span class="token number">265.0</span><span class="token punctuation">,</span>
		<span class="token string">"Tax"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token punctuation">{</span>
			<span class="token string">"Code"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
			<span class="token string">"Rate"</span><span class="token punctuation">:</span> <span class="token number">13.00</span><span class="token punctuation">,</span>
			<span class="token string">"Amount"</span><span class="token punctuation">:</span> <span class="token number">34.45</span><span class="token punctuation">,</span>
			<span class="token string">"Exoneration"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token string">"DocumentType"</span><span class="token punctuation">:</span> <span class="token string">"01"</span><span class="token punctuation">,</span>
				<span class="token string">"DocumentNumber"</span><span class="token punctuation">:</span> <span class="token string">"100"</span><span class="token punctuation">,</span>
				<span class="token string">"InstitutionName"</span><span class="token punctuation">:</span> <span class="token string">"Ministerio de Hacienda"</span><span class="token punctuation">,</span>
				<span class="token string">"IssueDate"</span><span class="token punctuation">:</span> <span class="token string">"2016-09-26T13:00:00+06:00"</span><span class="token punctuation">,</span>
				<span class="token string">"TaxAmount"</span><span class="token punctuation">:</span> <span class="token number">130</span><span class="token punctuation">,</span>
				<span class="token string">"PurchasePercentage"</span><span class="token punctuation">:</span> <span class="token number">10</span>
			<span class="token punctuation">}</span>
		<span class="token punctuation">}</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
		<span class="token string">"TotalLineAmount"</span><span class="token punctuation">:</span> <span class="token number">299.45</span>
	<span class="token punctuation">}</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
	<span class="token string">"Summary"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token string">"Currency"</span><span class="token punctuation">:</span> <span class="token string">"USD"</span><span class="token punctuation">,</span>
		<span class="token string">"ExchangeRate"</span><span class="token punctuation">:</span> <span class="token number">570.31</span><span class="token punctuation">,</span>
		<span class="token string">"TotalTaxedService"</span><span class="token punctuation">:</span> <span class="token number">478.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalExemptService"</span><span class="token punctuation">:</span> <span class="token number">0.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalTaxedGoods"</span><span class="token punctuation">:</span> <span class="token number">0.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalExemptGoods"</span><span class="token punctuation">:</span> <span class="token number">0.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalTaxed"</span><span class="token punctuation">:</span> <span class="token number">478.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalExempt"</span><span class="token punctuation">:</span> <span class="token number">0.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalSale"</span><span class="token punctuation">:</span> <span class="token number">478.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalDiscounts"</span><span class="token punctuation">:</span> <span class="token number">0.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalNetSale"</span><span class="token punctuation">:</span> <span class="token number">478.0</span><span class="token punctuation">,</span>
		<span class="token string">"TotalTaxes"</span><span class="token punctuation">:</span> <span class="token number">62.14</span><span class="token punctuation">,</span>
		<span class="token string">"TotalVoucher"</span><span class="token punctuation">:</span> <span class="token number">540.14</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"Reference"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
	<span class="token string">"Other"</span><span class="token punctuation">:</span> <span class="token keyword">null</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="anexo-de-tablas">Anexo de tablas</h2>
<p>Tablas requeridas para el envio de la Factura Electrónica</p>
<h3 id="tabla-1">Tabla #1</h3>

<table>
<thead>
<tr>
<th>Tipo de comprobante o documento asociado</th>
<th align="center">Código</th>
</tr>
</thead>
<tbody>
<tr>
<td>Factura electrónica</td>
<td align="center">01</td>
</tr>
<tr>
<td>Nota de débito electrónica</td>
<td align="center">02</td>
</tr>
<tr>
<td>Nota de crédito electrónica</td>
<td align="center">03</td>
</tr>
<tr>
<td>Tiquete Electrónico</td>
<td align="center">04</td>
</tr>
<tr>
<td>Confirmación de aceptación del comprobante electrónico</td>
<td align="center">05</td>
</tr>
<tr>
<td>Confirmación de aceptación parcial del comprobante electrónico</td>
<td align="center">06</td>
</tr>
<tr>
<td>Confirmación de rechazo del comprobante electrónico</td>
<td align="center">07</td>
</tr>
</tbody>
</table><h3 id="tabla-2">Tabla #2</h3>

<table>
<thead>
<tr>
<th>Condición de la venta</th>
<th align="center">Código</th>
</tr>
</thead>
<tbody>
<tr>
<td>Contado</td>
<td align="center">01</td>
</tr>
<tr>
<td>Crédito</td>
<td align="center">02</td>
</tr>
<tr>
<td>Consignación</td>
<td align="center">03</td>
</tr>
<tr>
<td>Apartado</td>
<td align="center">04</td>
</tr>
<tr>
<td>Arrendamiento con opción de compra</td>
<td align="center">05</td>
</tr>
<tr>
<td>Arrendamiento en función financiera</td>
<td align="center">06</td>
</tr>
<tr>
<td>Otros (se debe indicar la condición de la venta)</td>
<td align="center">99</td>
</tr>
</tbody>
</table><h3 id="tabla-3">Tabla #3</h3>

<table>
<thead>
<tr>
<th align="center">Código</th>
<th align="center">Tipo de identificación</th>
<th>Longitud</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">01</td>
<td align="center">Cedula Física</td>
<td>Debe de contener 9 dígitos, sin cero al inicio y sin guiones.</td>
</tr>
<tr>
<td align="center">02</td>
<td align="center">Cedula Jurídica</td>
<td>Debe contener 10 dígitos, sin cero al inicio y sin guiones.</td>
</tr>
<tr>
<td align="center">03</td>
<td align="center">DIMEX</td>
<td>Debe contener 11 o 12 dígitos, sin ceros al inicio y sin guiones</td>
</tr>
<tr>
<td align="center">04</td>
<td align="center">NITE</td>
<td>Debe contener 10 dígitos, sin ceros al inicio y sin guiones</td>
</tr>
</tbody>
</table><h3 id="tabla-4">Tabla #4</h3>

<table>
<thead>
<tr>
<th>Tipo de código de producto/servicio</th>
<th align="center">Código</th>
</tr>
</thead>
<tbody>
<tr>
<td>Código del producto del vendedor</td>
<td align="center">01</td>
</tr>
<tr>
<td>Código del producto del comprador</td>
<td align="center">02</td>
</tr>
<tr>
<td>Código del producto asignado por la industria</td>
<td align="center">03</td>
</tr>
<tr>
<td>Código uso interno</td>
<td align="center">04</td>
</tr>
<tr>
<td>Otros</td>
<td align="center">99</td>
</tr>
</tbody>
</table><h3 id="tabla-5">Tabla #5</h3>

<table>
<thead>
<tr>
<th>Impuesto</th>
<th align="center">Código</th>
</tr>
</thead>
<tbody>
<tr>
<td>Impuesto General sobre las Ventas</td>
<td align="center">01</td>
</tr>
<tr>
<td>Impuesto Selectivo de Consumo</td>
<td align="center">02</td>
</tr>
<tr>
<td>Impuesto Único a los combustibles</td>
<td align="center">03</td>
</tr>
<tr>
<td>Impuesto específico de Bebidas Alcohólicas</td>
<td align="center">04</td>
</tr>
<tr>
<td>Impuesto Específico sobre las bebidas envasadas sin contenido alcohólico y jabones de tocador</td>
<td align="center">05</td>
</tr>
<tr>
<td>Impuesto a los Productos de Tabaco</td>
<td align="center">06</td>
</tr>
<tr>
<td>Servicio</td>
<td align="center">07</td>
</tr>
<tr>
<td>Otros</td>
<td align="center">98</td>
</tr>
</tbody>
</table><h3 id="tabla-6">Tabla #6</h3>

<table>
<thead>
<tr>
<th>Excepción</th>
<th align="center">Código</th>
</tr>
</thead>
<tbody>
<tr>
<td>Impuesto General sobre las Ventas Diplomáticos</td>
<td align="center">08</td>
</tr>
<tr>
<td>Impuesto General sobre las Ventas Compras Autorizadas</td>
<td align="center">09</td>
</tr>
<tr>
<td>Impuesto General sobre las ventas Instituciones Públicas y otros Organismos</td>
<td align="center">10</td>
</tr>
<tr>
<td>Impuesto Selectivo de Consumo Compras Autorizadas</td>
<td align="center">11</td>
</tr>
<tr>
<td>Otros</td>
<td align="center">99</td>
</tr>
</tbody>
</table>
